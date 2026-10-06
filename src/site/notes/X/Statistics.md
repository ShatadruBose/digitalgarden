---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/x/statistics/","dgPassFrontmatter":true,"updated":"2026-10-05T19:07:11.776+05:30"}
---

<pre class="dataview dataview-error">Evaluation Error: SyntaxError: Invalid regular expression: missing /
    at DataviewInlineApi.eval (plugin:dataview:19027:21)
    at evalInContext (plugin:dataview:19028:7)
    at asyncEvalInContext (plugin:dataview:19035:16)
    at DataviewJSRenderer.render (plugin:dataview:19064:19)
    at DataviewJSRenderer.onload (plugin:dataview:18606:14)
    at e.load (app://obsidian.md/app.js:1:883194)
    at DataviewApi.executeJs (plugin:dataview:19607:18)
    at DataviewCompiler.eval (plugin:digitalgarden:10763:23)
    at next (&lt;anonymous&gt;)
    at eval (plugin:digitalgarden:90:61)</pre>/g) || []).length / 2;

    /* Wiki links */

    totalLinks += (
        content.match(/\[\[.*?\]\]/g) || []
    ).length;

    /* Images */

    totalImages += (
        content.match(/!\[.*?\]\(.*?\)/g) || []
    ).length;

    /* Newest note */

    const modified = toJSDate(
        file.stat?.mtime
    );

    const created = toJSDate(
        file.stat?.ctime
    );

    if (
        modified &&
        (
            !newestNote ||
            modified > toJSDate(
                newestNote.stat?.mtime
            )
        )
    ) {
        newestNote = file;
    }

    /* Oldest note */

    if (
        created &&
        (
            !oldestNote ||
            created < toJSDate(
                oldestNote.stat?.ctime
            )
        )
    ) {
        oldestNote = file;
    }
}

/* ================================================================
   TIME-BASED NOTE STATS
================================================================ */

let notesToday = 0;
let notesLast7Days = 0;
let notesLast30Days = 0;
let notesLastYear = 0;

let notesCreatedToday = 0;
let notesModifiedToday = 0;

let notesCreatedLast7Days = 0;
let notesModifiedLast7Days = 0;

let notesCreatedLast30Days = 0;
let notesModifiedLast30Days = 0;

for (const file of mdFiles) {

    const created = toJSDate(
        file.stat?.ctime
    );

    const modified = toJSDate(
        file.stat?.mtime
    );

    if (created) {

        if (isSameDay(created, now)) {
            notesCreatedToday++;
        }

        if (daysBetween(now, created) <= 7) {
            notesCreatedLast7Days++;
        }

        if (daysBetween(now, created) <= 30) {
            notesCreatedLast30Days++;
        }
    }

    if (modified) {

        if (isSameDay(modified, now)) {
            notesToday++;
            notesModifiedToday++;
        }

        if (daysBetween(now, modified) <= 7) {
            notesLast7Days++;
            notesModifiedLast7Days++;
        }

        if (daysBetween(now, modified) <= 30) {
            notesLast30Days++;
            notesModifiedLast30Days++;
        }

        if (daysBetween(now, modified) <= 365) {
            notesLastYear++;
        }
    }
}

/* ================================================================
   TAGS / METADATA
================================================================ */

const allTags = [];
const allAliases = [];

let notesWithTags = 0;
let notesWithoutTags = 0;

let notesWithAliases = 0;

let totalFrontmatterFields = 0;

for (const page of pages) {

    const tags = page.file?.tags || [];

    if (tags.length > 0) {
        notesWithTags++;

        for (const tag of tags) {
            allTags.push(tag);
        }
    } else {
        notesWithoutTags++;
    }

    const aliases = page.file?.aliases || [];

    const aliasArray = Array.isArray(aliases)
        ? aliases
        : [aliases];

    if (aliasArray.length > 0) {
        notesWithAliases++;

        for (const alias of aliasArray) {
            if (alias) {
                allAliases.push(alias);
            }
        }
    }

    if (page.file?.frontmatter) {
        totalFrontmatterFields +=
            Object.keys(
                page.file.frontmatter
            ).length;
    }
}

const uniqueTags = unique(allTags);
const uniqueAliases = unique(allAliases);

/* ================================================================
   LINK STATS
================================================================ */

let incomingLinks = 0;
let outgoingLinks = 0;

const linkedNotes = new Set();
const orphanNotes = [];

for (const page of pages) {

    const inlinks =
        page.file?.inlinks?.length || 0;

    const outlinks =
        page.file?.outlinks?.length || 0;

    incomingLinks += inlinks;
    outgoingLinks += outlinks;

    if (inlinks > 0 || outlinks > 0) {
        linkedNotes.add(page.file.path);
    }
}

for (const page of pages) {

    const inlinks =
        page.file?.inlinks?.length || 0;

    const outlinks =
        page.file?.outlinks?.length || 0;

    if (inlinks === 0 && outlinks === 0) {
        orphanNotes.push(page);
    }
}

/* ================================================================
   TASK STATS
================================================================ */

let totalTasks = 0;
let completedTasks = 0;
let incompleteTasks = 0;

for (const page of pages) {

    const tasks =
        page.file?.tasks || [];

    totalTasks += tasks.length;

    for (const task of tasks) {

        if (task.completed) {
            completedTasks++;
        } else {
            incompleteTasks++;
        }
    }
}

const taskCompletion =
    totalTasks
        ? (completedTasks / totalTasks) * 100
        : 0;

/* ================================================================
   FOLDER STATS
================================================================ */

const folderMap = new Map();

for (const file of files) {

    const folder = folderOf(file.path);

    folderMap.set(
        folder,
        (folderMap.get(folder) || 0) + 1
    );
}

const largestFolder =
    [...folderMap.entries()]
        .sort((a, b) => b[1] - a[1])[0];

/* ================================================================
   FILE TYPES
================================================================ */

const extensionMap = new Map();

for (const file of files) {

    const extension =
        file.extension.toLowerCase() || "none";

    extensionMap.set(
        extension,
        (extensionMap.get(extension) || 0) + 1
    );
}

const mostCommonExtension =
    [...extensionMap.entries()]
        .sort((a, b) => b[1] - a[1])[0];

/* ================================================================
   VAULT AGE
================================================================ */

let oldestDate = null;

for (const file of files) {

    const created = toJSDate(
        file.stat?.ctime
    );

    if (
        created &&
        (
            !oldestDate ||
            created < oldestDate
        )
    ) {
        oldestDate = created;
    }
}

const vaultAgeDays =
    oldestDate
        ? daysBetween(now, oldestDate)
        : 0;

const vaultAgeYears =
    vaultAgeDays / 365.25;

/* ================================================================
   AVERAGES
================================================================ */

const averageWords =
    totalNotes
        ? totalWords / totalNotes
        : 0;

const averageCharacters =
    totalNotes
        ? totalCharacters / totalNotes
        : 0;

const averageHeadings =
    totalNotes
        ? totalHeadings / totalNotes
        : 0;

const averageLinks =
    totalNotes
        ? totalLinks / totalNotes
        : 0;

const averageTasks =
    totalNotes
        ? totalTasks / totalNotes
        : 0;

/* ================================================================
   STATS
================================================================ */

const stats = [

    // VAULT

    ["Vault", "🗃️", "Total Files",
        formatNumber(totalFiles)],

    ["Vault", "📝", "Markdown Notes",
        formatNumber(totalNotes)],

    ["Vault", "📎", "Attachments",
        formatNumber(attachmentCount)],

    ["Vault", "📁", "Folders",
        formatNumber(folderCount)],

    ["Vault", "💾", "Vault Size",
        formatBytes(totalSize)],

    ["Vault", "📊", "Average File Size",
        formatBytes(averageFileSize)],

    ["Vault", "🗂️", "Largest File",
        largestFile
            ? formatBytes(largestFile.stat.size)
            : "—"],

    ["Vault", "📄", "Smallest File",
        smallestFile
            ? formatBytes(smallestFile.stat.size)
            : "—"],

    ["Vault", "📆", "Vault Age",
        `${vaultAgeYears.toFixed(1)} years`],

    ["Vault", "📅", "Vault Age",
        `${formatNumber(vaultAgeDays)} days`],

    // NOTES

    ["Notes", "📖", "Non-Empty Notes",
        formatNumber(nonEmptyNotes)],

    ["Notes", "⬜", "Empty Notes",
        formatNumber(emptyNotes)],

    ["Notes", "📈", "Non-Empty %",
        percent(nonEmptyNotes, totalNotes)],

    ["Notes", "📉", "Empty %",
        percent(emptyNotes, totalNotes)],

    ["Notes", "🆕", "Created Today",
        formatNumber(notesCreatedToday)],

    ["Notes", "✏️", "Modified Today",
        formatNumber(notesModifiedToday)],

    ["Notes", "🗓️", "Created — 7 Days",
        formatNumber(notesCreatedLast7Days)],

    ["Notes", "📝", "Modified — 7 Days",
        formatNumber(notesModifiedLast7Days)],

    ["Notes", "🗓️", "Created — 30 Days",
        formatNumber(notesCreatedLast30Days)],

    ["Notes", "📝", "Modified — 30 Days",
        formatNumber(notesModifiedLast30Days)],

    ["Notes", "📅", "Modified — 1 Year",
        formatNumber(notesLastYear)],

    ["Notes", "📌", "Newest Note",
        newestNote
            ? newestNote.name
            : "—"],

    ["Notes", "🏛️", "Oldest Note",
        oldestNote
            ? oldestNote.name
            : "—"],

    // CONTENT

    ["Content", "🔤", "Total Words",
        formatNumber(Math.round(totalWords))],

    ["Content", "🔡", "Characters",
        formatNumber(totalCharacters)],

    ["Content", "🔠", "Characters — No Spaces",
        formatNumber(totalCharactersNoSpaces)],

    ["Content", "📜", "Total Lines",
        formatNumber(totalLines)],

    ["Content", "📚", "Total Headings",
        formatNumber(totalHeadings)],

    ["Content", "💻", "Code Blocks",
        formatNumber(Math.round(totalCodeBlocks))],

    ["Content", "🔗", "Wiki Links",
        formatNumber(totalLinks)],

    ["Content", "🖼️", "Markdown Images",
        formatNumber(totalImages)],

    ["Content", "📖", "Average Words / Note",
        formatNumber(Math.round(averageWords))],

    ["Content", "🔤", "Average Characters / Note",
        formatNumber(Math.round(averageCharacters))],

    ["Content", "📚", "Average Headings / Note",
        averageHeadings.toFixed(1)],

    ["Content", "🔗", "Average Links / Note",
        averageLinks.toFixed(1)],

    // LINKS

    ["Links", "↙️", "Incoming Links",
        formatNumber(incomingLinks)],

    ["Links", "↗️", "Outgoing Links",
        formatNumber(outgoingLinks)],

    ["Links", "🕸️", "Linked Notes",
        formatNumber(linkedNotes.size)],

    ["Links", "🔗", "Linked %",
        percent(linkedNotes.size, totalNotes)],

    ["Links", "👻", "Orphan Notes",
        formatNumber(orphanNotes.length)],

    ["Links", "👻", "Orphan %",
        percent(orphanNotes.length, totalNotes)],

    // TAGS

    ["Tags", "#️⃣", "Unique Tags",
        formatNumber(uniqueTags.length)],

    ["Tags", "🏷️", "Tag Assignments",
        formatNumber(allTags.length)],

    ["Tags", "📌", "Tagged Notes",
        formatNumber(notesWithTags)],

    ["Tags", "📍", "Untagged Notes",
        formatNumber(notesWithoutTags)],

    ["Tags", "📊", "Tagged %",
        percent(notesWithTags, totalNotes)],

    ["Tags", "🏷️", "Unique Aliases",
        formatNumber(uniqueAliases.length)],

    ["Tags", "🔖", "Notes With Aliases",
        formatNumber(notesWithAliases)],

    // TASKS

    ["Tasks", "☑️", "Total Tasks",
        formatNumber(totalTasks)],

    ["Tasks", "✅", "Completed Tasks",
        formatNumber(completedTasks)],

    ["Tasks", "⬜", "Incomplete Tasks",
        formatNumber(incompleteTasks)],

    ["Tasks", "📊", "Completion Rate",
        `${taskCompletion.toFixed(1)}%`],

    ["Tasks", "📋", "Average Tasks / Note",
        averageTasks.toFixed(1)],

    // STRUCTURE

    ["Structure", "📁", "Largest Folder",
        largestFolder
            ? largestFolder[0]
            : "—"],

    ["Structure", "📦", "Files In Largest Folder",
        largestFolder
            ? formatNumber(largestFolder[1])
            : "0"],

    ["Structure", "🧩", "File Types",
        formatNumber(extensionMap.size)],

    ["Structure", "📄", "Most Common Type",
        mostCommonExtension
            ? `.${mostCommonExtension[0]}`
            : "—"],

    ["Structure", "📊", "Most Common Type Count",
        mostCommonExtension
            ? formatNumber(mostCommonExtension[1])
            : "0"],

    // METADATA

    ["Metadata", "🧾", "Frontmatter Fields",
        formatNumber(totalFrontmatterFields)],

    ["Metadata", "🏷️", "Unique Tags",
        formatNumber(uniqueTags.length)],

    // SYSTEM

    ["System", "⚡", "Scan Time",
        `${(performance.now() - startTime).toFixed(0)} ms`],

    ["System", "🧠", "Pages Indexed",
        formatNumber(pages.length)]
];

/* ================================================================
   STYLING
================================================================ */

const root = dv.container;

root.innerHTML = "";

const style = document.createElement("style");

style.textContent = `
.vault-stats-wrapper {
    width: 100%;
    font-family: var(--font-interface);
}

.vault-stats-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;

    margin-bottom: 22px;
    padding: 20px 22px;

    border: 1px solid
        var(--background-modifier-border);

    border-radius: 18px;

    background:
        linear-gradient(
            135deg,
            color-mix(
                in srgb,
                var(--interactive-accent) 10%,
                transparent
            ),
            transparent 55%
        ),
        var(--background-secondary);
}

.vault-stats-title {
    margin: 0;

    font-size: 1.7em;
    font-weight: 800;

    letter-spacing: -0.03em;
}

.vault-stats-subtitle {
    margin-top: 5px;

    color: var(--text-muted);
    font-size: 0.85em;
}

.vault-stats-total {
    display: flex;

    align-items: center;
    justify-content: center;

    min-width: 90px;
    min-height: 70px;

    padding: 8px 14px;

    border-radius: 15px;

    background:
        var(--background-primary);

    border: 1px solid
        var(--background-modifier-border);

    font-size: 1.7em;
    font-weight: 800;

    color:
        var(--interactive-accent);
}

.vault-stats-section {
    margin: 25px 0;
}

.vault-stats-section-title {
    display: flex;

    align-items: center;

    gap: 9px;

    margin-bottom: 12px;

    font-size: 1.05em;
    font-weight: 800;
}

.vault-stats-grid {
    display: grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(175px, 1fr)
        );

    gap: 10px;
}

.vault-stat-card {
    position: relative;

    min-width: 0;

    padding: 15px;

    border:
        1px solid
        var(--background-modifier-border);

    border-radius: 14px;

    background:
        var(--background-secondary);

    transition:
        transform 0.15s ease,
        border-color 0.15s ease,
        box-shadow 0.15s ease;

    overflow: hidden;
}

.vault-stat-card::before {
    content: "";

    position: absolute;

    inset: 0;

    background:
        linear-gradient(
            135deg,
            color-mix(
                in srgb,
                var(--interactive-accent) 7%,
                transparent
            ),
            transparent 65%
        );

    pointer-events: none;
}

.vault-stat-card:hover {
    transform: translateY(-2px);

    border-color:
        var(--interactive-accent);

    box-shadow:
        0 7px 25px rgba(0,0,0,0.08);
}

.vault-stat-icon {
    position: relative;

    font-size: 1.25em;

    margin-bottom: 9px;
}

.vault-stat-label {
    position: relative;

    color: var(--text-muted);

    font-size: 0.75em;

    text-transform: uppercase;

    letter-spacing: 0.055em;

    font-weight: 700;
}

.vault-stat-value {
    position: relative;

    margin-top: 5px;

    font-size: 1.25em;

    line-height: 1.25;

    font-weight: 800;

    color: var(--text-normal);

    overflow-wrap: anywhere;
}

.vault-stats-footer {
    margin-top: 25px;

    padding: 12px 15px;

    border-radius: 12px;

    background:
        var(--background-secondary);

    color: var(--text-muted);

    text-align: center;

    font-size: 0.75em;
}

@media (max-width: 600px) {

    .vault-stats-header {
        padding: 15px;
    }

    .vault-stats-title {
        font-size: 1.35em;
    }

    .vault-stats-total {
        min-width: 65px;
        min-height: 55px;

        font-size: 1.2em;
    }

    .vault-stats-grid {
        grid-template-columns:
            repeat(
                2,
                minmax(0, 1fr)
            );
    }

    .vault-stat-card {
        padding: 12px;
    }
}
`;

root.appendChild(style);

/* ================================================================
   DASHBOARD HEADER
================================================================ */

const wrapper = document.createElement("div");

wrapper.className =
    "vault-stats-wrapper";

const header = document.createElement("div");

header.className =
    "vault-stats-header";

header.innerHTML = `
    <div>

        <div class="vault-stats-title">
            📊 Vault Statistics
        </div>

        <div class="vault-stats-subtitle">
            ${formatNumber(stats.length)}
            statistics •
            ${formatNumber(totalNotes)}
            notes •
            ${formatBytes(totalSize)}
        </div>

    </div>

    <div class="vault-stats-total">
        ${formatNumber(stats.length)}
    </div>
`;

wrapper.appendChild(header);

/* ================================================================
   GROUP STATS
================================================================ */

const grouped = {};

for (const stat of stats) {

    const [
        category,
        icon,
        label,
        value
    ] = stat;

    if (!grouped[category]) {
        grouped[category] = [];
    }

    grouped[category].push({
        icon,
        label,
        value
    });
}

/* ================================================================
   RENDER
================================================================ */

for (
    const [category, categoryStats]
    of Object.entries(grouped)
) {

    const section =
        document.createElement("section");

    section.className =
        "vault-stats-section";

    const title =
        document.createElement("div");

    title.className =
        "vault-stats-section-title";

    title.innerHTML = `
        <span>
            ${escapeHTML(category)}
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            ${categoryStats.length}
        </span>
    `;

    section.appendChild(title);

    const grid =
        document.createElement("div");

    grid.className =
        "vault-stats-grid";

    for (const stat of categoryStats) {

        const card =
            document.createElement("div");

        card.className =
            "vault-stat-card";

        card.innerHTML = `
            <div class="vault-stat-icon">
                ${escapeHTML(stat.icon)}
            </div>

            <div class="vault-stat-label">
                ${escapeHTML(stat.label)}
            </div>

            <div
                class="vault-stat-value"
                title="${escapeHTML(stat.value)}"
            >
                ${escapeHTML(stat.value)}
            </div>
        `;

        grid.appendChild(card);
    }

    section.appendChild(grid);

    wrapper.appendChild(section);
}

/* ================================================================
   FOOTER
================================================================ */

const footer =
    document.createElement("div");

footer.className =
    "vault-stats-footer";

footer.innerHTML = `
    Automatically calculated from the current vault
    • Last scanned
    ${new Date().toLocaleTimeString()}
`;

wrapper.appendChild(footer);

root.appendChild(wrapper);
```
---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/x/statistics/","dgPassFrontmatter":true,"updated":"2026-10-05T19:07:11.776+05:30","dg-note-properties":{"tags":null,"aliases":null}}
---

<style>
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
</style><div class="vault-stats-wrapper"><div class="vault-stats-header">
    <div>

        <div class="vault-stats-title">
            📊 Vault Statistics
        </div>

        <div class="vault-stats-subtitle">
            62
            statistics •
            1,454
            notes •
            1.73 GB
        </div>

    </div>

    <div class="vault-stats-total">
        62
    </div>
</div><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Vault
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            10
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🗃️
            </div>

            <div class="vault-stat-label">
                Total Files
            </div>

            <div class="vault-stat-value" title="4,653">
                4,653
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📝
            </div>

            <div class="vault-stat-label">
                Markdown Notes
            </div>

            <div class="vault-stat-value" title="1,454">
                1,454
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📎
            </div>

            <div class="vault-stat-label">
                Attachments
            </div>

            <div class="vault-stat-value" title="3,199">
                3,199
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📁
            </div>

            <div class="vault-stat-label">
                Folders
            </div>

            <div class="vault-stat-value" title="1,214">
                1,214
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                💾
            </div>

            <div class="vault-stat-label">
                Vault Size
            </div>

            <div class="vault-stat-value" title="1.73 GB">
                1.73 GB
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📊
            </div>

            <div class="vault-stat-label">
                Average File Size
            </div>

            <div class="vault-stat-value" title="390 KB">
                390 KB
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🗂️
            </div>

            <div class="vault-stat-label">
                Largest File
            </div>

            <div class="vault-stat-value" title="435 MB">
                435 MB
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📄
            </div>

            <div class="vault-stat-label">
                Smallest File
            </div>

            <div class="vault-stat-value" title="0 B">
                0 B
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📆
            </div>

            <div class="vault-stat-label">
                Vault Age
            </div>

            <div class="vault-stat-value" title="1.8 years">
                1.8 years
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📅
            </div>

            <div class="vault-stat-label">
                Vault Age
            </div>

            <div class="vault-stat-value" title="645 days">
                645 days
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Notes
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            13
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📖
            </div>

            <div class="vault-stat-label">
                Non-Empty Notes
            </div>

            <div class="vault-stat-value" title="1,418">
                1,418
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ⬜
            </div>

            <div class="vault-stat-label">
                Empty Notes
            </div>

            <div class="vault-stat-value" title="36">
                36
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📈
            </div>

            <div class="vault-stat-label">
                Non-Empty %
            </div>

            <div class="vault-stat-value" title="97.5%">
                97.5%
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📉
            </div>

            <div class="vault-stat-label">
                Empty %
            </div>

            <div class="vault-stat-value" title="2.5%">
                2.5%
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🆕
            </div>

            <div class="vault-stat-label">
                Created Today
            </div>

            <div class="vault-stat-value" title="3">
                3
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ✏️
            </div>

            <div class="vault-stat-label">
                Modified Today
            </div>

            <div class="vault-stat-value" title="9">
                9
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🗓️
            </div>

            <div class="vault-stat-label">
                Created — 7 Days
            </div>

            <div class="vault-stat-value" title="16">
                16
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📝
            </div>

            <div class="vault-stat-label">
                Modified — 7 Days
            </div>

            <div class="vault-stat-value" title="21">
                21
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🗓️
            </div>

            <div class="vault-stat-label">
                Created — 30 Days
            </div>

            <div class="vault-stat-value" title="345">
                345
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📝
            </div>

            <div class="vault-stat-label">
                Modified — 30 Days
            </div>

            <div class="vault-stat-value" title="532">
                532
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📅
            </div>

            <div class="vault-stat-label">
                Modified — 1 Year
            </div>

            <div class="vault-stat-value" title="1,175">
                1,175
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📌
            </div>

            <div class="vault-stat-label">
                Newest Note
            </div>

            <div class="vault-stat-value" title="Illusions.md">
                Illusions.md
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🏛️
            </div>

            <div class="vault-stat-label">
                Oldest Note
            </div>

            <div class="vault-stat-value" title="Note Temple.md">
                Note Temple.md
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Content
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            12
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔤
            </div>

            <div class="vault-stat-label">
                Total Words
            </div>

            <div class="vault-stat-value" title="1,120,520">
                1,120,520
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔡
            </div>

            <div class="vault-stat-label">
                Characters
            </div>

            <div class="vault-stat-value" title="7,758,429">
                7,758,429
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔠
            </div>

            <div class="vault-stat-label">
                Characters — No Spaces
            </div>

            <div class="vault-stat-value" title="6,342,753">
                6,342,753
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📜
            </div>

            <div class="vault-stat-label">
                Total Lines
            </div>

            <div class="vault-stat-value" title="361,960">
                361,960
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📚
            </div>

            <div class="vault-stat-label">
                Total Headings
            </div>

            <div class="vault-stat-value" title="23,943">
                23,943
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                💻
            </div>

            <div class="vault-stat-label">
                Code Blocks
            </div>

            <div class="vault-stat-value" title="2,850">
                2,850
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔗
            </div>

            <div class="vault-stat-label">
                Wiki Links
            </div>

            <div class="vault-stat-value" title="2,179">
                2,179
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🖼️
            </div>

            <div class="vault-stat-label">
                Markdown Images
            </div>

            <div class="vault-stat-value" title="7">
                7
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📖
            </div>

            <div class="vault-stat-label">
                Average Words / Note
            </div>

            <div class="vault-stat-value" title="771">
                771
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔤
            </div>

            <div class="vault-stat-label">
                Average Characters / Note
            </div>

            <div class="vault-stat-value" title="5,336">
                5,336
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📚
            </div>

            <div class="vault-stat-label">
                Average Headings / Note
            </div>

            <div class="vault-stat-value" title="16.5">
                16.5
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔗
            </div>

            <div class="vault-stat-label">
                Average Links / Note
            </div>

            <div class="vault-stat-value" title="1.5">
                1.5
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Links
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            6
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ↙️
            </div>

            <div class="vault-stat-label">
                Incoming Links
            </div>

            <div class="vault-stat-value" title="1,444">
                1,444
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ↗️
            </div>

            <div class="vault-stat-label">
                Outgoing Links
            </div>

            <div class="vault-stat-value" title="2,113">
                2,113
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🕸️
            </div>

            <div class="vault-stat-label">
                Linked Notes
            </div>

            <div class="vault-stat-value" title="537">
                537
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔗
            </div>

            <div class="vault-stat-label">
                Linked %
            </div>

            <div class="vault-stat-value" title="36.9%">
                36.9%
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                👻
            </div>

            <div class="vault-stat-label">
                Orphan Notes
            </div>

            <div class="vault-stat-value" title="917">
                917
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                👻
            </div>

            <div class="vault-stat-label">
                Orphan %
            </div>

            <div class="vault-stat-value" title="63.1%">
                63.1%
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Tags
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            7
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                #️⃣
            </div>

            <div class="vault-stat-label">
                Unique Tags
            </div>

            <div class="vault-stat-value" title="176">
                176
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🏷️
            </div>

            <div class="vault-stat-label">
                Tag Assignments
            </div>

            <div class="vault-stat-value" title="1,318">
                1,318
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📌
            </div>

            <div class="vault-stat-label">
                Tagged Notes
            </div>

            <div class="vault-stat-value" title="812">
                812
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📍
            </div>

            <div class="vault-stat-label">
                Untagged Notes
            </div>

            <div class="vault-stat-value" title="642">
                642
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📊
            </div>

            <div class="vault-stat-label">
                Tagged %
            </div>

            <div class="vault-stat-value" title="55.8%">
                55.8%
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🏷️
            </div>

            <div class="vault-stat-label">
                Unique Aliases
            </div>

            <div class="vault-stat-value" title="45">
                45
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🔖
            </div>

            <div class="vault-stat-label">
                Notes With Aliases
            </div>

            <div class="vault-stat-value" title="47">
                47
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Tasks
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            5
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ☑️
            </div>

            <div class="vault-stat-label">
                Total Tasks
            </div>

            <div class="vault-stat-value" title="96">
                96
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ✅
            </div>

            <div class="vault-stat-label">
                Completed Tasks
            </div>

            <div class="vault-stat-value" title="9">
                9
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ⬜
            </div>

            <div class="vault-stat-label">
                Incomplete Tasks
            </div>

            <div class="vault-stat-value" title="87">
                87
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📊
            </div>

            <div class="vault-stat-label">
                Completion Rate
            </div>

            <div class="vault-stat-value" title="9.4%">
                9.4%
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📋
            </div>

            <div class="vault-stat-label">
                Average Tasks / Note
            </div>

            <div class="vault-stat-value" title="0.1">
                0.1
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Structure
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            5
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📁
            </div>

            <div class="vault-stat-label">
                Largest Folder
            </div>

            <div class="vault-stat-value" title="Notes/07 Journals (Calender)/Daily Notes">
                Notes/07 Journals (Calender)/Daily Notes
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📦
            </div>

            <div class="vault-stat-label">
                Files In Largest Folder
            </div>

            <div class="vault-stat-value" title="500">
                500
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🧩
            </div>

            <div class="vault-stat-label">
                File Types
            </div>

            <div class="vault-stat-value" title="27">
                27
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📄
            </div>

            <div class="vault-stat-label">
                Most Common Type
            </div>

            <div class="vault-stat-value" title=".md">
                .md
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                📊
            </div>

            <div class="vault-stat-label">
                Most Common Type Count
            </div>

            <div class="vault-stat-value" title="1,454">
                1,454
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            Metadata
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            2
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🧾
            </div>

            <div class="vault-stat-label">
                Frontmatter Fields
            </div>

            <div class="vault-stat-value" title="14,159">
                14,159
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🏷️
            </div>

            <div class="vault-stat-label">
                Unique Tags
            </div>

            <div class="vault-stat-value" title="176">
                176
            </div>
        </div></div></section><section class="vault-stats-section"><div class="vault-stats-section-title">
        <span>
            System
        </span>

        <span style="
            color: var(--text-faint);
            font-size: 0.75em;
            font-weight: 500;
        ">
            2
        </span>
    </div><div class="vault-stats-grid"><div class="vault-stat-card">
            <div class="vault-stat-icon">
                ⚡
            </div>

            <div class="vault-stat-label">
                Scan Time
            </div>

            <div class="vault-stat-value" title="273 ms">
                273 ms
            </div>
        </div><div class="vault-stat-card">
            <div class="vault-stat-icon">
                🧠
            </div>

            <div class="vault-stat-label">
                Pages Indexed
            </div>

            <div class="vault-stat-value" title="1,454">
                1,454
            </div>
        </div></div></section><div class="vault-stats-footer">
    Automatically calculated from the current vault
    • Last scanned
    22:21:20
</div></div>
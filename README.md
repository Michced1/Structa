# Structa

Structa is an offline desktop application for creating and managing factions, organizations, units, ranks, and personnel. You can use it to create factions for fun, develop organizations for stories and roleplay, recreate fictional or historical factions, or help manage an actual group with actual people.

Your faction might be a club, police service, military organization, government department, or fictional institution. You define its ranks, hierarchy, positions, uniforms, awards, and members rather than using one fixed organizational model. Members belong to units, ranks determine seniority, eligible members fill positions, awards contribute points, and service history records changes. Graphs, reports, and staffing tools help you understand and develop the organization.

The current package is a **portable Windows application**. It runs locally without an online account and stores each organization in a separate SQLite database. For real groups, it is a local roster and planning tool; it does not currently provide an online member portal, shared accounts, or automatic synchronization between computers.

## Contents

1. [Installation and first launch](#1-installation-and-first-launch)
2. [Create or open an organization](#2-create-or-open-an-organization)
3. [Understand the workspace](#3-understand-the-workspace)
4. [Build your first faction](#4-build-your-first-faction)
5. [Find, view, and edit members](#5-find-view-and-edit-members)
6. [Recruitment and name files](#6-recruitment-and-name-files)
7. [Assignments and transfers](#7-assignments-and-transfers)
8. [Ranks, points, and promotions](#8-ranks-points-and-promotions)
9. [Units, command, and positions](#9-units-command-and-positions)
10. [Awards and history](#10-awards-and-history)
11. [Attire, colors, and images](#11-attire-colors-and-images)
12. [Structure diagrams](#12-structure-diagrams)
13. [Statistics and exports](#13-statistics-and-exports)
14. [CSV import](#14-csv-import)
15. [Advanced staffing and scenarios](#15-advanced-staffing-and-scenarios)
16. [Options and shortcuts](#16-options-and-shortcuts)
17. [Backups, restoration, and moving data](#17-backups-restoration-and-moving-data)
18. [Troubleshooting](#18-troubleshooting)
19. [Suggested everyday workflow](#19-suggested-everyday-workflow)
20. [Further documentation](#20-further-documentation)

## 1. Installation and first launch

### Requirements

- A Windows computer capable of running the supplied executable.
- The complete release folder, including `Structa.exe` and `_internal`.
- A writable location for databases and backups.

**Python, Qt, SQLite, and a separate database server do not need to be installed for this portable release.** Required runtime files are included. Normal use is offline.

### Install the current package

1. Download the complete application archive. On GitHub, choose the packaged application attached to a release.
2. Right-click the downloaded archive and choose **Extract All**.
3. Extract to a normal folder, such as `Documents\Structa`.
4. Check that `Structa.exe` and `_internal` are beside each other.
5. Double-click **Structa.exe**.
6. Read the getting-started window if shown. Reopen it through **Help → Getting started**.
7. Create or open an organization using the next section.

Do not run from inside the compressed archive. Keep the entire extracted folder together. Copying only the executable leaves required files behind. To launch from your desktop, create a **shortcut** to the executable. This portable package has no separate installation wizard.

### Release folder

```text
Structa/
├── Structa.exe       Application launcher
├── _internal/       Required runtime and application files
├── README.md        This guide
├── docs/            Additional manuals
├── names/           Recruitment name files
└── saves/           Empty folder for your own organizations
```

Keep `_internal` intact. Your databases can live elsewhere.

The public release starts without saved organizations or personal data. Create a database through **File → New Database**, or open an existing database through **File → Open Database**. Files ending in `.bak` are backups, rather than normal starting files. Before experimenting with an existing organization, copy its entire folder, including images.

### Updating

1. Make complete backups of your organizations.
2. Close Structa.
3. Extract the new release into a separate folder.
4. Run its executable and open your existing database.
5. Let compatibility checks and supported upgrades finish. Protective backups are created before supported database upgrades.
6. Check records and images before removing the older application copy.

Do not replace your own saves with the new release's sample saves. Application files and organization data are separate.

## 2. Create or open an organization

### Create a database

1. Choose **File → New Database**, or press **Ctrl+N**.
2. Choose a writable folder. A separate folder per faction makes assets easier to manage.
3. Enter an unused filename, such as `MyFaction.db`.
4. Confirm creation.
5. Define your ranks, unit types, units, and members.

A new organization contains the structural **Government** root and system event types. It does not generate ranks or people for you. Creation requires an unused filename to avoid overwriting another organization.

### Open or close a database

Choose **File → Open Database** or **Ctrl+O**, select a `.db` file, and wait for checks to finish. Then select a unit or open **Personnel → All personnel**.

**File → Close Database** detaches the organization without exiting. Opening another database switches the organization being edited.

### Saving

Confirmed actions save directly to the database. There is no separate document-style Save operation after every edit.

Imports, reviewed promotions, and staffing plans have their own confirmation/apply controls. Previewing or canceling does not apply the proposal. Some quick actions apply immediately, as explained below.

Use backups for recoverable earlier states. Do not assume every confirmed action has a general Undo command.

## 3. Understand the workspace

| Tab | Purpose |
| --- | --- |
| **Organization** | Navigate units, inspect command cards, manage members and positions. |
| **Unit structure** | View the hierarchy as a diagram. |
| **Rank progression** | View levels, groups, insignia, and progression branches. |
| **Statistics** | Explore personnel, points, coverage, awards, activity, and data checks. |
| **Options** | Customize appearance, workspace, defaults, shortcuts, and backups. |

### Organization tree

The left tree contains Government, its subordinate units, and **Unassigned recruits**. Expand branches and select a unit to inspect its command information, **Members**, and **Positions**.

A member's **direct unit** is their actual assignment. A unit's **subtree** includes the selected unit and all descendants. These scopes produce different lists and counts.

Enable **View → Show directly assigned member counts** for labels such as `Alpha (12)`. That counts direct members, excluding people assigned only to subunits.

### Common controls

- Type into search fields to narrow lists.
- Click a table heading to sort; click again to reverse.
- Ctrl-click selects separate rows; Shift-click selects a range.
- Right-click rows for available actions.
- Double-click a member for their profile.
- Drag column borders to resize. Where supported, right-click headings to choose visible columns.
- Use **View → Expand tree / Collapse tree** for hierarchy navigation.
- Press **F5** or choose **View → Refresh** to refresh the organization.

Filters affect display, not assignments or position eligibility.

### Search everything

Press **Ctrl+K**, or choose **Edit → Find records and actions**. Type a name or keyword, select a result, and press Enter or double-click. Esc closes the search.

Results can open profiles, navigate to units, edit definitions, or launch actions such as recruitment, imports, backups, and scenarios.

## 4. Build your first faction

Start with a small working structure before adding complexity.

### Create rank groups

Open **Ranks → Manage rank groups**. Add categories such as Members, Supervisors, Officers, or Specialists.

| Field | Meaning |
| --- | --- |
| Name | Displayed category name. |
| Description | Optional explanation. |
| Display order | Optional unique integer controlling group presentation. |
| Color | Color used for the group's ranks. |

Display order does not determine seniority. Rank level and authority do that.

### Create ranks

Open **Ranks → Manage ranks**. For a simple test, create Recruit at level 1, Member at level 2, and Leader at level 3. Choose their groups and promotion points. Add descriptions, abbreviations, paygrades, insignia, or attire later.

Create ranks before unit types, because command rules reference them. See section 8 for field details.

### Create a unit type

Open **Units → Manage unit types** and add a type such as Team.

1. Enter name, optional description, and color.
2. Check at least one valid commander rank, such as Leader.
3. Optionally check deputy ranks.
4. If deputies are enabled, set **Default deputy places**.
5. Confirm.

A **unit type** is reusable; a **unit** is an instance, such as Alpha Team. Several units can share a type.

### Create a unit

1. Select Government.
2. Right-click **New subordinate unit**, or use the Units menu.
3. Choose your type.
4. Enter a custom name, optional number, and description.
5. Check the parent and confirm.

Government is structural and does not automatically select a commander.

### Recruit and assign

1. Open **Personnel → Recruit personnel**.
2. Choose an academy/rank group and entry rank.
3. Browse to a file in the release's `names` folder.
4. Enter a small intake count and base-points range.
5. Confirm.
6. Open Unassigned recruits, select members, and choose **Assign / transfer**.
7. Choose your unit and confirm.

Open a profile, try a reviewed promotion, and inspect the command card and Positions tab. This establishes the basic cycle: define, recruit, assign, and manage careers.

## 5. Find, view, and edit members

### Lists and filters

Use a unit's Members tab for local work, **Personnel → All personnel** for the whole database, or **Personnel → Unassigned recruits** for people awaiting assignment. Clear filters when someone seems missing.

**Include subordinate units** adds descendants' members. When it is off, the default still includes subunit people who hold a position in the selected unit. Disable **Show this unit’s position holders when subordinate units are excluded** under **Options → Organization** for a strictly direct-members-only list. This does not change assignments or counts.

### Profiles

Double-click a member or choose **Details / awards**. Profiles combine identity, rank/insignia, unit path, points, positions, attire, awards, and history. They open on **Service history**; select an entry for its complete report. The separate Attire panel explains the resolved uniform and source.

### Edit personal information

Use **Edit person** for first name, surname, direct unit, base points, attire override, and position limit. Existing rank is protected here: use **Promote / demote** so rewards and consequences are handled consistently.

For actual people, replace generated names through editing or import prepared personnel records. Generated identities do not have to be retained.

### Delete a member

Select the member, choose Delete, and review confirmation. Their active record is removed, while history remains with identifying snapshots and a cleared live link. To retain the record without an assignment, unassign or transfer instead.

## 6. Recruitment and name files

Each group acts as an **academy**. Entry ranks are its ranks at the lowest seniority level.

### Create an intake

1. Choose **Personnel → Recruit personnel**.
2. Select academy and entry rank; choose the intended branch if several entry ranks exist.
3. Set inclusive minimum/maximum base points. Equal values give everyone identical starting base points.
4. Enter a count from **1 to 10,000**.
5. Choose a first-name or full-name file.
6. Optionally choose a separate surname file.
7. Confirm.

Recruits start unassigned with zero service years. History records academy, source files, and points. An intake saves together, so failure leaves no partial batch.

### File format

Use UTF-8 text smaller than 5 MB, with one name or full name per line. Blank lines and lines starting with `#` are ignored.

```text
# First names
Alex
Jordan
Morgan
```

Or use complete pairs:

```text
Alex Carter
Jordan Reed
Morgan Ellis
```

Full-name pairs stay together when no separate surname file is selected. With single names and no surname file, both parts are drawn from the same list. Choose separate files for distinct pools.

The release contains `names/USNames.txt`, `names/PLImiona.txt`, and `names/PLNazwiska.txt`. Use Browse if the default location does not show them. For Polish generation, select first names and surnames separately. Repeated names are possible; this is random generation, not a unique-identity check.

## 7. Assignments and transfers

### Destination picker

1. Select one or more members.
2. Choose **Assign / transfer**.
3. Search or expand the hierarchy.
4. Check the full path, unit type, and direct count.
5. Choose the destination and confirm.

Transfers change direct assignment and can change command, positions, and automatic attire. Use the workflow's unassigned choice to retain people without a direct unit. Unassigned members hold no unit positions.

### Drag and drop

Drag selected members from the main table onto a unit in the left tree. Hover over collapsed units to expand them.

**Dropping applies the transfer immediately** and records history. Check the target before releasing. The Unassigned recruits heading is not a drop destination, and cross-database drags are rejected.

If someone still appears under a parent afterward, check Direct unit: subordinate membership and position-holder display can include them without changing assignment.

## 8. Ranks, points, and promotions

### Rank fields

Open **Ranks → Manage ranks**.

| Field | Use |
| --- | --- |
| Name | Full displayed name. |
| NATO / paygrade | Optional descriptive grade. |
| Short name / Abbreviation | Alternate labels. |
| Description | Explanation. |
| Seniority level | Higher number means greater seniority. |
| Authority at equal level | Breaks ties between same-level ranks. |
| Rank group | Category/color. |
| Points awarded per promotion to this rank | Reward contributing to promotion through this rank. |
| Rank ratio (auto-promotion weight) | Independent distribution weight, default 100. Zero excludes this rank in Rank ratio mode. |
| Default attire | Fallback uniform. |
| Insignia image | Visual identifier. |

IDs, paygrade text, and group order do not determine seniority. Equal levels can represent branches. Selectors generally show lower levels first for convenience; command favors higher seniority.

### Points

```text
Total points = base points + current values of all assigned awards
```

Base points include recruitment, promotion rewards, and adjustments. Repeated awards each count. History describes already-applied changes; do not add its entries again. Points help order comparable members but **do not automatically promote anybody**.

### Find candidates

**Personnel → Promotion candidates** starts with highest total points first. Filter by unit/group/rank and inspect candidates before changing them.

### Quick promotion

Select one member and choose **Promote one rank**. The next distinct level is used, even across numeric gaps. One destination applies immediately; multiple alternatives open a chooser whose selection applies without another confirmation. Use the reviewed workflow for detailed consequences first.

### Reviewed changes

1. Choose **Promote / demote** for the member.
2. Select promotion, demotion, or equivalent-level switch.
3. Choose the destination. The single-member workflow permits changes spanning multiple levels.
4. Review path, rewards, group transitions, and affected positions.
5. Check gains, losses, replacements, and recommendations in the direct unit and relevant ancestors.
6. Choose **Confirm rank change**, or cancel.

A promotion can displace someone else from a calculated role.

### Rewards and years

Bonuses exclude the current rank. Multi-level promotion includes one rank at every existing intermediate level and the selected destination. The lowest-point alternative is used at intermediate branching levels. Read the preview for exact rewards.

For example, promotion from level 1 to level 4 through existing levels 2 and 3 includes bonuses from the chosen level-2, level-3, and level-4 ranks.

Each confirmed promotion adds random **1–4 service years**, once per action regardless of levels crossed. Demotions/equivalent switches leave years unchanged. Previewing/canceling adds nothing.

Demotions and equivalent switches award no bonus and remove no previous points. Promoting later awards a bonus again. Editing a rank's bonus affects future promotions, not rewards already added to base points.

### Batch changes

1. Select multiple members with Ctrl/Shift.
2. Choose quick promotion or Promote / demote.
3. Choose destinations for groups sharing a current rank.
4. Skip groups that should remain unchanged.
5. In the full batch dialog, adjust direction and adjacent-level controls as needed.
6. Review and confirm.

The changes/history save together. Stale previews require fresh review.

## 9. Units, command, and positions

### Edit or move units

Select a unit and choose **Units → Edit / move selected unit**, **Edit → Edit selected unit**, or right-click Edit / move. Change name, number, description, color, type, or parent. Changing parent moves the subtree; cycles are blocked.

Delete only units without children/direct staff. Government is protected. **Units → All units (sortable)** gives a flat list with direct and total counts.

### Command selection

Command roles are calculated from personnel in the relevant scope, subject to position limits. They are not permanent manual appointments in the command card.

Selection order is higher level, higher authority, higher total points, then lower personnel ID.

Default command uses the type's rank choices; several ranks can be valid. Inspect status/recommendation: default cards can show higher/lower/equivalent-grade or outside-options warnings rather than a perfect recommended match.

Deputies exclude the commander. Clear deputy ranks to disable default deputies; increase **Default deputy places** to permit several. The overview shows filled/total places and lets you select each deputy and open their profile.

### Define positions

Open **Units → Manage unit-type positions**, or a unit's **Positions → Configure positions**.

Set type, name, description, eligible ranks, Places per unit, priority, and optional Command role. Definitions belong to types; every unit of that type shares the rules but calculates its own occupants.

Command fills first. Regular positions fill by priority, lower numbers first, then creation order for ties. Eligible members are ordered by level, authority, points, and ID. Regular positions accept only configured ranks. Unfilled places remain vacant. One person holds at most one position in a unit.

### Designate command positions

Set **Command role → Commander** or **Deputy** on a named definition.

- Commander has exactly one place; Deputy may have several.
- Each type can designate one position for each role.
- The named position and corresponding card share occupants.
- Named Deputy capacity replaces the default capacity.
- Clearing/deleting a designation restores default rules.

Deputies cannot also occupy regular positions in the same unit. Designated command positions are not counted twice in personnel summaries.

### Position limit

Default **Position limit = 1** permits a position in the direct unit only. In a profile, change the limit and choose **Apply limit**, or edit it through Edit person.

A value of 5 permits one position in the direct unit plus one in each of four nearest parents, subject to eligibility and vacancies. Empty/incompatible positions do not extend the window farther upward. Limits apply to all command/regular roles. Unassigned people hold none.

### Inspect and rename

Search Positions by title, rank, or member, filter vacancies, and double-click for complete occupants/profile links. Hover over truncated text. Personnel tables offer Positions and Position count columns. Changes to assignments, ranks, points, awards, and rules recalculate occupants.

For a local title, select a unit's position and choose **Rename in this unit**. This affects that unit's displays, not shared capacity/eligibility/priority. Clear the title to inherit again. Shared renames update inheriting units; local overrides remain. Deleting a shared definition removes it across the type while retaining members.

## 10. Awards and history

### Create and grant awards

Open **Awards → Manage awards**. Define a name, value, description, and optional image. The manager also provides recipient information.

1. Open a member's profile and awards section.
2. Choose **Grant award**.
3. Select the award and enter its citation/reason.
4. Confirm.

The same award can be granted repeatedly; every occurrence contributes points. **Edit assignment** changes assignment details. **Remove assignment** removes that occurrence and its point contribution. Double-click to preview an award image.

Changing the definition's point value changes all current recipients' totals immediately. This differs from promotion bonuses already added to base points. Award assignments have no separate award-date field in the current model; history provides context.

### Automatic service history

Profiles open on Service history with date/time, type, point change, and summary. Select an entry for the complete report and before/after details. Search to find particular actions.

Supported actions record recruitment, edits, transfers, promotions, adjustments, awards, attire, and affected positions. Earlier history is not invented for actions predating tracking. Changes and their history save together: failure to record history rolls back the action.

### Custom events

1. Open a profile and choose **Add custom event**.
2. Choose or create an event type.
3. Enter date/time and notes.
4. Optionally enter a signed base-points adjustment.
5. Review and confirm.

Use this for training, deployments, battles, injuries, commendations, roleplay milestones, or other records. Positive adjustments add base points; negative ones subtract. Backdated adjustments still affect current points when applied.

Use **Personnel → Manage event types** to edit reusable labels/colors. Used types cannot be deleted. History is append-only: add a correction event rather than rewriting an earlier entry.

### Global activity

**Personnel → Global activity** opens Activity with current-personnel filters cleared and unlinked history included. Filter dates, types, and text; double-click entries for complete reports. Profile date display is configurable; statistical date filtering and exports remain UTC.

## 11. Attire, colors, and images

### Attire templates

Open **Attire → Manage attires**. Enter a name, optional unit type, and text descriptions for **hat, torso, legs, and equipment**. Every component is optional. Templates can describe uniforms, ceremonial clothing, or specialist equipment.

Set a fallback **Default attire** in a rank definition. For a specific combination, open **Attire → Unit type / rank attire rules** and choose the exact type, rank, and template.

Effective attire resolves in this order:

1. Personal override.
2. Rule for the direct unit's type and exact current rank.
3. Rank default.
4. No configured attire.

Rules use the direct unit, not a parent's type. Unassigned members cannot match a unit-type rule.

### Personal attire

Choose **Change attire** in the profile's separate Attire panel. Select automatic inheritance, an existing template, or custom components. Custom saves create personal copies without modifying shared templates.

Clear the override to restore automatic resolution. Transfers/promotions recalculate inherited attire; personal overrides remain. Used templates cannot be deleted until relevant personal overrides, rank defaults, and rules are cleared.

### Colors

Rank groups supply rank colors. Unit types supply unit colors; individual units can override them. Blank unit color inherits from its **unit type**, not its parent.

Use the picker or enter a hex value. Relevant lists, selectors, trees, and diagrams use these colors.

### Images

Use Browse in rank and award editors. Selected files are copied alongside the database:

```text
MyFaction.db
MyFaction_assets/
```

Keep both together. Missing images show text placeholders. External image references remain external and require separate care when moving or backing up.

## 12. Structure diagrams

### Unit structure

Parents appear above children, connected by branches. Cards show name, type, direct population, and total including subunits. Hover for the path; double-click a unit to edit it. Hierarchy/staffing changes refresh the graph. Unassigned people do not count toward units.

### Rank progression

Ranks appear at distinct levels in group panels, with colors, insignia, paygrades, and promotion points. Equal-level alternatives share a row, with branches indicating next-level options. Hover for authority/group/description, and double-click to edit. Viewing an arrow does not promote a member.

### Navigation

- Left-drag anywhere, including cards, to pan.
- Use mouse wheel or **+ / −** to zoom.
- **Actual size** returns to 100%.
- **Recenter** centers and fits the entire drawing.

## 13. Statistics and exports

Statistics reads the database without changing personnel. Application edits invalidate its snapshot; **Refresh data** also picks up external edits.

### Available views

| View | Use |
| --- | --- |
| Overview | Headcounts, assignments, decorations, points, years, command coverage, vacancies, activity totals. |
| Explorer | Custom groupings/measures and chart/table drilldowns. |
| Personnel | Current records, point components, years, awards, roles, next-level options. |
| Units | Paths, depth, direct/subtree populations, command status and recommendations. |
| Ranks / Rank groups / Unit types | Definition usage and summaries, including unused definitions. |
| Awards / Award grants | Values, grants, recipients, repeated awards, citations. |
| Timeline / Event types / Activity | Time summaries, event distributions, individual activity. |
| Attires / Attire rules | Templates, components, wearers, assignments. |
| Data checks | Missing fields/images, empty units/groups, unused ranks, unlinked history, and review items. |

Navigation groups related reports under Summary, People and organization, Awards, History, Attire, and Checks.

### Filters

Combine unit/subtree, unit type, rank/group, assignment, command role, awards, search, and point/year ranges. Activity has additional date/type/text filters.

Choose your population, then the report. Clear filters before treating results as organization-wide totals. Double-click relevant definition rows to filter, or a person to open their profile.

### Explorer workflow

1. Choose a grouping: rank, type, assignment, years, point band, attire, or another available dimension.
2. Optionally add a second grouping.
3. Choose a measure such as headcount, total/average/median points, years, or award recipients.
4. Adjust point/year band sizes as applicable.
5. Click a chart bar or double-click a group to inspect its members.

The chart shows the largest twenty groups; the table includes all groups. Changing filters/refreshing clears temporary drilldowns.

### Presets and exports

Save a named preset for repeated use. It retains global filters, dates, grouping, measures, band sizes, and report selection. Presets are scoped to the database path, so moving a database can affect availability.

**Export visible table** writes UTF-8 CSV of searched/sorted rows using visible columns.

**Export all reports** writes a ZIP with all fifteen globally filtered CSV reports and interpretation notes. It includes all report rows/columns regardless of local search, hidden columns, or temporary drilldown.

### Read results correctly

- Parent/subtree populations overlap; do not sum them as separate populations.
- Command calculations use the full relevant population even when filters hide people.
- Activity dates filter events, not reconstructed historical staffing. Current rank/unit labels describe current records.
- Award grants have no separate date, so current award totals are not filtered by award date.
- History points describe applied changes, not additional current points.
- Unlinked history cannot satisfy current-personnel filters when current rank/unit is unknown.
- Data checks are review aids: an intentionally empty unit or unused rank is not necessarily an error.

## 14. CSV import

**File → Import CSV** creates personnel, ranks, rank groups, unit types, units, or award definitions from UTF-8 CSV/TSV. Comma, semicolon, and tab separators are supported. Limits are **10 MB and 10,000 records per file**.

### Prepare the file

Include a header row. Import groups before ranks, ranks before unit types referencing them, types before units, and personnel last. Hierarchical unit parents should precede their children unless already present.

References accept IDs or exact names; units support full paths. Ambiguous names are rejected, so use IDs/paths when needed.

### Import steps

1. Choose destination record type and source file.
2. Map headers to destination fields.
3. Supply required fields; blank mappings use available defaults.
4. Preview and inspect invalid rows/duplicates.
5. Correct mapping or file and preview again as needed.
6. Apply only after review.

Imports **create records, not updates to existing ones**. Possible duplicates are rejected unless **Skip possible duplicates** is selected. Personnel duplicate detection compares name, surname, rank, and unit; it is a heuristic rather than an identity system.

Preview creates nothing live. Apply checks freshness and saves records/history together. A stale preview must be regenerated.

## 15. Advanced staffing and scenarios

Use these tools after establishing ranks, units, and positions.

### Auto-promote to positions

1. Select members in a personnel list.
2. Choose **Auto-promote to positions**.
3. Choose a unit type and desired positions.
4. Choose **Point ratio** or **Rank ratio** under **Distribution based on**, and review the suggested distribution.
5. Optionally select **Enter ratios manually**.
6. Inspect Desired/Actual counts, individual promotions, cumulative rewards, and position consequences.
7. Apply the reviewed plan.

**Point ratio** uses inverse destination promotion points: 100 and 200 points suggest a 2:1 spread. **Rank ratio** (the default) uses the independent ratio saved under Ranks → Manage ranks directly: 200 and 100 suggest a 2:1 spread. New and existing ranks default to ratio 100, giving equal shares. Rank ratio works even when promotion points are zero. Both modes still award the usual cumulative promotion points. Manual ratios may be decimals; zero excludes a rank and at least one must be positive. Manual weights are required for zero/missing promotion points only in Point ratio mode. Switching modes restores that mode's calculated weights.

The planner promotes upward or retains already eligible ranks; it does not demote or switch equivalent ranks. Members too senior remain unchanged. Constraints can prevent exact desired ratios, so inspect Actual counts.

Assignments stay unchanged. Preparation does not guarantee occupancy: seniority, eligibility, limits, and capacity still apply.

### Create or fill from a sister unit

Open **Units → Create / fill from sister unit**, also available by right-clicking a unit. Compatible sisters share a parent and unit type.

1. Choose a source sister whose current structure/direct rank counts form the template.
2. Choose new sister creation or filling an existing compatible sister.
3. Set name files, entry ranks, and starting point ranges.
4. Choose whether to reuse unassigned personnel.
5. Review subunits, assignments, recruitment, and promotions.
6. Apply.

Missing subunits are created recursively, while existing members/excess staff remain. Matching uses type and number/name, with an unambiguous single-child fallback. Resolve ambiguous structures first.

By default, exact-rank unassigned staff are reused first, then suitable promotions/equivalent switches. Higher ranks are never demoted. Remaining vacancies are recruited at entry ranks and promoted as required. Disable pool reuse to recruit missing staff instead.

This copies a structure, not identities, awards, points, or experience. Normal promotion rewards/years apply. Changes/history save together; stale plans require fresh review.

### Staffing forecast and scenarios

Choose **Units → Staffing forecast and scenarios** to work on a private copy.

1. Inspect current staffing.
2. Stage rank changes and assignments.
3. Optionally recruit at an academy entry rank using a name file.
4. Assign scenario recruits: they start unassigned with zero base points.
5. Compare current/proposed populations and vacancies.
6. Choose **Apply reviewed scenario**.

Concrete bonuses, years, and history are calculated in the scenario. Applying retains those reviewed results without rerolling years. **Reset scenario** discards the plan and reloads current data. Closing without applying discards the copy.

Apply checks freshness and saves changes together. Do not sum all vacancy columns: named command roles may appear both as named-position vacancies and command vacancies. Parent counts overlap with descendants.

## 16. Options and shortcuts

Preferences persist for your Windows user independently of organization databases.

### Appearance/workspace

Set dark mode, high contrast, text size, and compact/comfortable rows. Workspace options remember window geometry, panel widths, expanded units, and selection. Choose a startup tab and optionally reopen the last database.

Table layouts can retain column order, widths, visibility, and sorting. At least one column remains visible.

### Organization/dates/confirmations

Set default sorting, counts, subordinate membership, and whether subunit position holders appear when subordinate membership is off. These preferences do not rewrite assignments.

Deletion confirmations are enabled by default. Additional bulk confirmations are optional because reviewed previews already exist. Profile dates can show local time or UTC in three formats; statistics date filters/exports remain UTC.

Automatic backups are initially off; configure them below.

### Default keys

| Keys | Action |
| --- | --- |
| Ctrl+N | New database. |
| Ctrl+O | Open database. |
| Ctrl+K | Find records/actions. |
| F5 | Refresh organization. |
| Alt+F4 | Close application. |
| Ctrl-click / Shift-click | Multiple row selection. |

Search/open/new shortcuts are editable with conflict checks. Use configured keys if changed.

## 17. Backups, restoration, and moving data

### Complete backups

1. Open your organization.
2. Choose **File → Backups and restore**.
3. Choose **Back up now**.
4. Check the backup location.

The ZIP contains a consistent database snapshot and adjacent `<database-stem>_assets` files. External references remain external; arbitrary images elsewhere are not included.

### Automatic complete backups

Enable in Options and choose interval, folder, and retention count. The timer operates while Structa is open with a database attached, not when closed. Retention removes only automatic backups for that source database; manual complete backups stay.

Keep a copy outside the application folder for protection against losing the whole folder.

### Database-only backups

**File → Backup Database** creates an SQLite copy at an unused filename, without images. Open it through **File → Open Database**.

### Restore complete backups

1. Open Backups and restore.
2. Select the complete backup and restoration action.
3. Choose an unused destination, preferably a new folder.
4. Allow validation and any supported upgrades on an isolated copy.
5. Inspect the restored organization when it opens.

Restore refuses to overwrite the original database or a conflicting assets folder.

### Move/share an organization

A complete backup is the simplest handoff for managed assets. For a direct move, close Structa and move the database with its matching assets and external references.

```text
MyFaction/
├── MyFaction.db
└── MyFaction_assets/
```

Preserve filenames and relative locations. Moving only the database can break pictures. Preferences are stored separately for the Windows user, while presets are scoped to database paths.

For actual people, review records, citations, history, images, and exports before sharing. Sharing a database provides an independent copy, not a synchronized connection.

### Upgrade backups

Files named `.pre-history-...bak`, `.pre-positions-...bak`, and similar are protective copies before specific compatibility changes. They are separate from complete ZIP backups. Retain them until you have checked the upgraded organization.

## 18. Troubleshooting

### Application does not start / missing files

Extract the full archive again. Keep `_internal` beside `Structa.exe` and launch outside the archive. Check that shortcuts still target the complete folder.

### There is no launch.bat

Start this release with **Structa.exe**. Python/virtual-environment/source-launcher instructions apply to a separate source checkout and are not needed here.

### Database or backup cannot be created

Use a writable folder and unused filename. Do not overwrite an organization or restore over its original.

### Recruitment fails

Create groups/ranks first. Choose a lowest-level entry rank, valid UTF-8 file under 5 MB, count of 1–10,000, and minimum points no greater than maximum.

### Recruits are missing

They start unassigned. Assign from Unassigned recruits. If already assigned, clear filters and check selected unit/subordinate-membership behavior.

### Unexpected position holder

Check assignment, position limit, eligible ranks, capacity, priority, and competing members' level/authority/points. Command fills first; a person cannot hold several positions in one unit.

### Can I manually appoint a named position?

Occupants are calculated from eligibility, scope, ordering, limits, and capacity. Adjust the relevant definitions or records and inspect results. Positions is not a free-form appointment list.

### Command changed after an award

Award values affect points, which break ties between comparable candidates. Transfers, rank changes, and rule edits can also change occupants.

### Command recommendation warning

Review member rank, type choices, and designated command positions. Default recommendations and exact named-position eligibility are different rules.

### List is larger than direct count

It may include descendants or subunit position holders. Direct counts only include direct assignments.

### Award edit changed many totals

Current occurrences all use the definition's current value. Repeated grants each count. Promotion rewards already added to base points are not retroactively recalculated in this manner.

### Missing images after moving

Move the matching assets folder too and check external locations. Complete backups include adjacent managed assets, not unrelated external files.

### Stale preview

The organization changed after review. Reload, preview again, and inspect the new result before applying.

### Cannot delete a definition/unit

Read the message for active references or structural protection. Units must have no children/direct staff; used templates/event types also have restrictions. Clear/move relevant relationships first.

### Unexpected statistics

Clear global filters, local search, and drilldowns; check direct/subtree scope and refresh. Do not add overlapping populations or count history point changes again.

### Several people editing online

The current release is local. Exchanging files creates separate copies with no automatic merging. Keep a clear authoritative copy if sharing files between maintainers.

## 19. Suggested everyday workflow

1. Open the correct organization.
2. Find the relevant unit/member.
3. Recruit or import newcomers and assign them.
4. Record events, awards, and reviewed rank changes.
5. Check command cards and vacancies after important changes.
6. Review reports or export when needed.
7. Make complete backups before large changes or sharing.

For larger factions, use reusable types/positions, sister-unit staffing, presets, and scenarios. A basic roster does not require attire or advanced planning; introduce those as needed.

## 20. Further documentation

- [User and compatibility manual](docs/manual.md): detailed semantics, reports, graphs, history, and database compatibility.
- [Settings, data tools, and planning](docs/new-tools.md): options, backups, imports, presets, position titles, and scenarios.
- **Help → Getting started**: the in-application introduction.

This guide describes the portable package and workflows in the accompanying manuals. Users do not need the source code to follow it.

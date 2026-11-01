<!-- Rapider Official App SOW & Specification | App #189: Church & Religious Organization Management (church-and-religious-organization-management) | Domain: IND -->

# #189 Church & Religious Organization Management (`church-and-religious-organization-management`) — Scope of Work (SOW)

- **App Number & Name:** `#189` — Church & Religious Organization Management
- **Proposed App Key:** `church-and-religious-organization-management`
- **Suite / Domain Key & Model Prefix:** `IND` (`Ind*`)
- **Representative Product (`P1`):** Planning Center
- **Combined Feature Catalog:** [../combined-features/189-church-and-religious-organization-management-features.md](../combined-features/189-church-and-religious-organization-management-features.md)
- **Target Release Posture:** Multi-Tradition Faith & Congregation Management, Cryptographic Child Check-In Safety, Worship & Volunteer Scheduling, Sacraments/Lifecycle, Clergy-Privileged Pastoral Care & Dual-Custody Tithes/Giving Handoff Microapplication

---

## 1. Executive Outcome & Target Audience

### 1.1 Business Problem Solved
Churches, parishes, synagogues, mosques, temples, and multi-campus faith communities face acute child-safety, clergy-confidentiality, volunteer burnout, and cash-stewardship risks when relying on paper child sign-in sheets without guardian pickup codes, scheduling youth volunteers whose background clearances have expired, storing sensitive pastoral counseling notes in shared spreadsheets visible to general volunteers, or counting weekend plate offerings without dual-custody verification. **Rapider Church & Religious Organization Management (`church-and-religious-organization-management`)** unifies family household directories, newcomer assimilation, cryptographic child check-in & custody safeguards, worship/liturgical run-of-show planning, volunteer scheduling, multi-tradition sacramental/lifecycle registries, strictly isolated pastoral care cases, and dual-custody tithes/offerings handoffs directly atop canonical Rapider `crm`, `payments`, `#188` (`nonprofit-donor-and-fundraising-management`), `acc`, `accpayable`, and `events` foundations.

### 1.2 Target Personas & Progressive Disclosure
- **SME Fast-Path Defaults (Local Single-Campus Congregations, Parishes, Synagogues, Community Centers, 50–400 Members):** Organize family households linked to `crm`, launch weekend child check-in badges with unique parent/child matching security codes and allergy tags, build weekly service orders and volunteer schedules, track small groups, and log dual-counter weekend offering batches synced cleanly to `#188` and `acc`.
- **Enterprise Progressive Disclosure (Multi-Campus Megachurches, Dioceses, Regional Religious Networks, 1,000–50,000+ Congregants):** Enforce mandatory youth volunteer background-check expiration locks, classroom adult-to-child ratio thresholds, official multi-tradition sacramental & Yahrzeit registries with certificate generation, clergy-only `CLERGY_CONFIDENTIAL` counseling vaults, benevolence direct-to-vendor disbursements via Home `WorkItem`s, anti-bias pastor giving masking, and GDPR Article 9 special-category religious-data consent governance.

### 1.3 Measurable Business Outcomes
- **100% Verified Child Pickup & Youth Volunteer Screening:** Zero unscreened volunteers scheduled into children's rooms and zero child check-outs completed without matching cryptographic security code + authorized guardian verification.
- **Zero Unauthorized Pastoral Care Disclosures:** Record-level `CLERGY_CONFIDENTIAL` isolation prevents IT admins, finance clerks, and volunteers from accessing sensitive counseling or bereavement notes.
- **100% Dual-Custody Plate & Offering Integrity:** Enforced two-counter sign-off (`primaryCounterUserId != secondaryVerifierUserId`) eliminates single-person cash-handling risk while automating tax statement handoffs to `#188` and GL journals to `acc`.

### 1.4 Benchmark Summary (`P1`–`P6`)
Synthesizes the worship run-of-show, volunteer scheduling, and child check-in safety UX of **`P1` Planning Center**, assimilation queues and digital giving agility of **`P2` Pushpay / CCB**, background-check gating, facility conflict checks, and pastoral ACL rigor of **`P3` Rock RMS**, multi-tradition sacramental, envelope, and Yahrzeit lifecycle depth of **`P4` ParishSOFT & ShulCloud**, canonical householding and GDPR Art. 9 governance of **`P5` Salesforce Nonprofit Cloud (Faith)**, and dual-custody multi-campus fund accounting handoffs of **`P6` Sage Intacct Faith-Based**.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### 2.1 In-Scope Capabilities
1. Congregational household & member directory (`IndCongregantProfile`) with opt-in directory privacy, newcomer assimilation `<rapider-kanban>`, child allergy/custody safeguards, and volunteer background-check clearance tracking.
2. Small groups, classes, and fellowship circles (`IndMinistryGroup`) with attendance tracking.
3. Cryptographic child check-in & guardian pickup verification (`IndChildCheckInSession`) with allergy badges, adult-to-child ratio checks, and emergency parent SMS/phone paging (`<rapider-phone-input>`).
4. Worship/liturgical service run-of-show builder (`IndServicePlan` + CCLI song/liturgy cues) and volunteer scheduling with block-out dates & background-check locks (`IndVolunteerAssignment`).
5. Multi-tradition sacramental & religious lifecycle milestone register (`IndSacramentRecord` — Baptism, Confirmation, Matrimony, Bar/Bat Mitzvah, Nikah, Yahrzeit).
6. Clergy-privileged confidential pastoral care & benevolence requests (`IndPastoralCareCase`) and dual-custody weekend tithe/plate/envelope batch verification (`IndGivingBatch`).

### 2.2 Out-of-Scope Capabilities (Delegated to Adjacent Rapider Apps)
- **Payment gateway card/ACH processing, statutory 501(c)(3)/CRA/Gift Aid tax receipt numbering, and multi-year capital campaign pledges:** Delegated to `payments` (`FinPaymentIntent`) and `#188 Nonprofit Donor & Fundraising Management` (`IndGiftTransaction`, `IndPledgeCommitment`, `IndTaxReceipt`).
- **General Ledger trial balance, clergy payroll/housing allowance withholding, and vendor check printing:** Owned by `acc` (`FinJournalEntry`), `payroll` (`HrPayrollRun`), and `accpayable` (`FinSupplierBill`).
- **Accredited K-12 parochial school gradebooks and state transcripts:** Owned by `#164 Student Information System (SIS)`.
- **Standalone custom approval inbox:** Delegated strictly to Rapider Platform Home `WorkItem`s.

### 2.3 Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Canonical Models) | Integration Contract with `church-and-religious-organization-management` |
| :--- | :--- | :--- |
| **`church-and-religious-organization-management` (`#189` — This App)** | `IndCongregantProfile`, `IndMinistryGroup`, `IndChildCheckInSession`, `IndServicePlan`, `IndVolunteerAssignment`, `IndSacramentRecord`, `IndPastoralCareCase`, `IndGivingBatch` | Owns congregational assimilation, child check-in security, worship/volunteer rosters, sacraments, pastoral care ACLs, and dual-custody offering batches. |
| **Core `crm` App (`CRM` Suite)** | `CrmAccount`, `CrmContact` | Family households bind to `CrmAccount.id` and individual congregants/guardians bind to `CrmContact.id`. |
| **`#188 Nonprofit Fundraising` (`IND`)** | `IndDonorProfile`, `IndGiftTransaction`, `IndRestrictedFund`, `IndTaxReceipt` | Verified `IndGivingBatch` envelope/tithe lines hand off to `#188` for donor hard-credit ledgering and consolidated year-end tax receipting. |
| **`acc` & `accpayable` (`FIN` Suite)** | `FinJournalEntry`, `FinSupplierBill` | Locked `IndGivingBatch` totals post balanced fund `FinJournalEntry`s; approved benevolence utility/rent aid creates vendor `FinSupplierBill`s without exposing pastoral notes. |
| **`events`, `hrs` & `assets` (`MKT`/`HR`/`OPS`)** | `MktEvent`, `HrLocation`, `OpsOperationsAsset` | Retreats/camps link to `MktEvent`; sanctuary/classroom bookings reference `HrLocation` and AV equipment `OpsOperationsAsset`. |
| **Rapider Platform Services** | Identity/RBAC, Home `WorkItem`, `projectChannelMessage`, Files | Lost-pickup-tag supervisor overrides and benevolence disbursements route via Home `WorkItem`s; sacramental certificates reside in Platform Files. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture

To comply strictly with the **Rapider Minimum 3 Items Sidebar Rule**, all visible pages are organized into **3 sidebar sections (`Overview`, `Ministry & Youth Safety`, `Care, Rites & Stewardship`) containing 3 visible items each (9 visible menu items total)**, while detail and drawer routes set `displayOnMenu: false`.

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `dashboard` | Congregation Hub | `Overview` | `true` (Order 1) | KPI cards (`countSWR`), weekend service & kids check-in attendance trends, volunteer coverage gaps, assimilation funnel, background-check expiry alerts. |
| 2 | `congregants` | People & Households | `Overview` | `true` (Order 2) | Searchable `IndCongregantProfile` directory (`findSWR`), `#activeFilterTagsBar` with `Clear all`, `<rapider-phone-input>` family contact, opt-in directory & background badges. |
| 3 | `assimilation-groups` | Assimilation & Groups | `Overview` | `true` (Order 3) | `<rapider-kanban>` newcomer assimilation pathway (`FIRST_VISIT` -> `SMALL_GROUP_JOINED`) + `IndMinistryGroup` fellowship/class directory & attendance %. |
| 4 | `child-checkin` | Child Check-In & Safety | `Ministry & Youth Safety` | `true` (Order 4) | Live `IndChildCheckInSession` classroom roster, room adult-to-child ratio bars, allergy/EpiPen chips, security-code pickup verification & parent SMS page button. |
| 5 | `service-plans` | Worship & Service Plans | `Ministry & Youth Safety` | `true` (Order 5) | `IndServicePlan` liturgical/worship calendar, timed run-of-show cues, song/CCLI arrangement summary, campus `HrLocation` room assignment. |
| 6 | `volunteer-rosters` | Volunteer Scheduling | `Ministry & Youth Safety` | `true` (Order 6) | `IndVolunteerAssignment` shift matrix, accept/decline/swap status, block-out conflict warnings, youth background-check gate status, >6-week burnout flags. |
| 7 | `pastoral-care` | Confidential Pastoral Care | `Care, Rites & Stewardship` | `true` (Order 7) | Clergy-ACL-isolated `IndPastoralCareCase` queue (hospital visits, bereavement, counseling), benevolence aid request trigger (hidden from unauthorized roles). |
| 8 | `sacraments-lifecycle` | Sacraments & Milestones | `Care, Rites & Stewardship` | `true` (Order 8) | Multi-tradition `IndSacramentRecord` register (Baptism, Matrimony, Bar/Bat Mitzvah, Nikah, Yahrzeit), register book/page ref, certificate PDF generator. |
| 9 | `giving-batches` | Tithes & Offering Batches | `Care, Rites & Stewardship` | `true` (Order 9) | Dual-custody `IndGivingBatch` counter (`Decimal128` envelope/loose cash/check/online splits), two-verifier lock status, `#188` & `FinJournalEntry` sync log. |
| 10 | `congregant-detail` | Household & Member 360 | *(Hidden)* | `false` | `IndCongregantProfile` view (`?id=...`), family tree, groups, serving schedule, authorized child pickup contacts, role-gated giving badge, `Back to list`. |
| 11 | `service-plan-detail` | Service Run-of-Show | *(Hidden)* | `false` | Minute-by-minute `IndServicePlan` cues, chord/liturgy attachments, assigned volunteers, `projectChannelMessage` production thread, `Back to list`. |
| 12 | `checkin-drawer` | Check-In / Verify Pickup | *(Hidden)* | `false` | Sliding drawer generating unique 4-char alphanumeric security code (`IndChildCheckInSession`) or verifying pickup code + guardian ID & custody block check. |
| 13 | `giving-batch-drawer` | Count / Verify Plate Batch | *(Hidden)* | `false` | Sliding drawer entering envelope/plate `Decimal128` counts, enforcing `primaryCounterUserId != secondaryVerifierUserId` before locking & `closePageDrawer()`. |

### Mandatory Rapider UI Standards Enforced Across All Pages
- **SWR-First Clean Reads:** Initial loads invoke `window.rapiderApi.findSWR` / `countSWR` with zero manual `isDeleted` filter clauses in API payloads and filter `item.isDeleted !== true` in memory.
- **Table Actions & Row Navigation:** Clicking primary identifiers (Member Name, Service Title, Check-In Code/Child Name, Sacrament Cert #, Batch Number) navigates to detail views (`font-semibold text-primary hover:underline cursor-pointer`). **Zero standalone "View" buttons** appear in `Actions`; rows render icon+text **Edit** and icon-only **Delete** (`title="Delete" aria-label="Delete"`).
- **Custom Elements & Contrast:** Guardian emergency paging and member mobile fields use `<rapider-phone-input>`, `#/assimilation-groups` uses `<rapider-kanban>`, all primary/danger buttons enforce `#ffffff !important` white text, and native browser `alert`/`confirm`/`prompt` are banned.

---

## 4. Canonical Data Models (`Ind*` — 8 Models)

All models belong to the `IND` domain (`Ind*` prefix), omit `projectId`, assign platform UUIDs (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in deterministic seeds), store monetary batch/benevolence/ratio figures as `Decimal128`, and track concurrency via `version`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`IndCongregantProfile`** | `id: UUID`, `memberCode: String`, `fullName: String`, `householdRole: Enum(HEAD, SPOUSE, ADULT_MEMBER, CHILD_MINOR)`, `birthDate: Date?`, `mobilePhone: String (E.164)?`, `envelopeNumber: String?`, `assimilationStage: Enum(FIRST_VISIT, WELCOME_CONNECT, FOUNDATIONS_CLASS, SERVING_ONBOARDED, SMALL_GROUP_JOINED)`, `membershipStatus: Enum(VISITOR, ACTIVE_MEMBER, YOUTH_MINOR, INACTIVE, TRANSFERRED)`, `directoryOptIn: Boolean`, `gdprArt9ConsentAt: DateTime?`, `allergyAndMedicalAlert: String?`, `authorizedPickupContactIds: UUID[]`, `restrictedCustodyBlockNames: String[]`, `backgroundCheckStatus: Enum(NOT_REQUIRED, PENDING, CLEARED, EXPIRED, REJECTED)`, `backgroundCheckExpiresAt: Date?`, `version: Int` | `crmContactId -> CrmContact.id`, `householdAccountId -> CrmAccount.id`, `campusLocationId -> HrLocation.id?`, `donorProfileId -> IndDonorProfile.id?` | `directoryOptIn` defaults to `false`; minors (`CHILD_MINOR`) are never exposed in public directories; if `backgroundCheckExpiresAt < today`, `backgroundCheckStatus` transitions to `EXPIRED`. |
| **`IndMinistryGroup`** | `id: UUID`, `groupCode: String`, `name: String`, `groupCategory: Enum(SMALL_GROUP, YOUTH_CLASS, ADULT_EDUCATION, CHOIR_WORSHIP, SERVING_TEAM)`, `requiresYouthClearance: Boolean`, `meetingScheduleText: String`, `maxCapacity: Int`, `memberIds: UUID[]`, `avgAttendancePct: Decimal128`, `status: Enum(OPEN, FULL, CLOSED_SEASON, ARCHIVED)`, `version: Int` | `leaderCongregantId -> IndCongregantProfile.id`, `roomLocationId -> HrLocation.id?` | If `requiresYouthClearance = true`, `leaderCongregantId` must hold `backgroundCheckStatus == CLEARED`. |
| **`IndChildCheckInSession`** | `id: UUID`, `sessionDate: Date`, `securityPickupCode: String`, `classroomName: String`, `allergyBadgePrinted: Boolean`, `checkedInAt: DateTime`, `checkedOutAt: DateTime?`, `lostTagOverrideUsed: Boolean`, `status: Enum(CHECKED_IN, PARENT_PAGED, CHECKED_OUT, INCIDENT_HOLD)`, `version: Int` | `childCongregantId -> IndCongregantProfile.id`, `checkedInByGuardianId -> IndCongregantProfile.id`, `checkedOutByGuardianId -> IndCongregantProfile.id?`, `servicePlanId -> IndServicePlan.id?`, `overrideWorkItemId -> WorkItem.id?` | Cryptographically random per-session `securityPickupCode` (never reused on same `sessionDate`); transitioning to `CHECKED_OUT` requires exact `securityPickupCode` match AND `checkedOutByGuardianId` in `authorizedPickupContactIds` (or approved supervisor `overrideWorkItemId` after photo-ID verification). |
| **`IndServicePlan`** | `id: UUID`, `planNumber: String`, `serviceTitle: String`, `traditionOrSeries: String`, `scheduledStartAt: DateTime`, `plannedDurationMinutes: Int`, `orderOfServiceJson: JSON`, `ccliSongRefs: String[]`, `adultHeadcount: Int`, `childCheckInCount: Int`, `onlineStreamCount: Int`, `status: Enum(DRAFT, REHEARSAL_READY, LIVE, COMPLETED)`, `version: Int` | `campusLocationId -> HrLocation.id`, `reservedAssetIds: UUID[]` | Prevents overlapping sanctuary/room `campusLocationId` bookings unless multi-room capacity permits. |
| **`IndVolunteerAssignment`** | `id: UUID`, `roleTitle: String`, `ministryArea: Enum(KIDS_YOUTH, WORSHIP_ARTS, AV_PRODUCTION, HOSPITALITY_USHER, LITURGY_LECTOR)`, `requiresBackgroundClearance: Boolean`, `responseStatus: Enum(INVITED, ACCEPTED, DECLINED, SUB_REQUESTED, CHECKED_IN)`, `consecutiveWeeksStreak: Int`, `version: Int` | `servicePlanId -> IndServicePlan.id`, `volunteerCongregantId -> IndCongregantProfile.id` | Hard safeguarding invariant: when `ministryArea == KIDS_YOUTH` or `requiresBackgroundClearance == true`, assigning a volunteer whose `backgroundCheckStatus != CLEARED` or whose clearance expires prior to `scheduledStartAt` is deterministically rejected. |
| **`IndSacramentRecord`** | `id: UUID`, `certificateNumber: String`, `riteType: Enum(BAPTISM, FIRST_COMMUNION, CONFIRMATION, MATRIMONY, ORDINATION, BAR_BAT_MITZVAH, BRIT_MILAH, NIKAH, YAHRZEIT_MEMORIAL, DEDICATION)`, `performedDate: Date`, `hebrewOrLiturgicalDate: String?`, `officiantName: String`, `witnessNames: String[]`, `registerBookRef: String`, `registerPageRef: String`, `certificateFileId: UUID?`, `isOfficialLocked: Boolean`, `version: Int` | `subjectCongregantId -> IndCongregantProfile.id`, `secondarySubjectId -> IndCongregantProfile.id?`, `campusLocationId -> HrLocation.id?` | Once `isOfficialLocked = true`, sacramental registry entries are append-only immutable (canonical marginal-notation amendments only). |
| **`IndPastoralCareCase`** | `id: UUID`, `caseNumber: String`, `careCategory: Enum(HOSPITAL_VISIT, BEREAVEMENT, MARRIAGE_COUNSELING, CRISIS_SPIRITUAL, BENEVOLENCE_AID, CONFIDENTIAL_PRAYER)`, `visibilityTier: Enum(CLERGY_CONFIDENTIAL, CARE_TEAM_RESTRICTED)`, `confidentialSummary: String`, `benevolenceRequestedAmt: Decimal128?`, `currencyCode: String?`, `payeeVendorAccountId: UUID?`, `status: Enum(OPEN, FOLLOW_UP_SCHEDULED, AID_PENDING_APPROVAL, CLOSED)`, `version: Int` | `congregantId -> IndCongregantProfile.id`, `assignedClergyUserId -> User.id`, `benevolenceWorkItemId -> WorkItem.id?`, `benevolenceBillId -> FinSupplierBill.id?` | Server-side query interceptor enforces `visibilityTier`: `CLERGY_CONFIDENTIAL` records are invisible to non-assigned / non-ordained roles and excluded from AI global search; benevolence handoffs pass only vendor + amount to `accpayable`, never `confidentialSummary`. |
| **`IndGivingBatch`** | `id: UUID`, `batchNumber: String`, `collectionDate: Date`, `sourceType: Enum(WEEKEND_PLATE_ENVELOPE, SPECIAL_OFFERING, HIGH_HOLIDAY_APPEAL, ZAKAT_COLLECTION)`, `expectedControlTotal: Decimal128`, `countedTotalAmount: Decimal128`, `looseCashAmount: Decimal128`, `envelopeLinesJson: JSON`, `currencyCode: String`, `primaryCounterUserId: UUID`, `secondaryVerifierUserId: UUID?`, `verifiedAt: DateTime?`, `status: Enum(OPEN_COUNTING, PENDING_SECOND_VERIFIER, VERIFIED_LOCKED, POSTED_TO_FINANCE)`, `version: Int` | `campusLocationId -> HrLocation.id?`, `restrictedFundId -> IndRestrictedFund.id`, `journalEntryId -> FinJournalEntry.id?` | Dual-custody invariant: cannot transition to `VERIFIED_LOCKED` or `POSTED_TO_FINANCE` unless `secondaryVerifierUserId != null`, `secondaryVerifierUserId != primaryCounterUserId`, and `countedTotalAmount == expectedControlTotal`. |

---

## 5. Core End-to-End User Journeys

### Journey 1: Weekend Child Check-In, Allergy Alert, Custody Safeguard & Verified Pickup
1. Guardian `Sarah Miller` arrives at `#/child-checkin` and checks in 6-year-old `Leo Miller` (`allergyAndMedicalAlert = "SEVERE PEANUT — EPIPEN IN BACKPACK"`, `restrictedCustodyBlockNames = [" Mark Vance "]`).
2. `ind.church.checkInChild` checks classroom `Kids-Room-B` adult-to-child ratio, generates unique 4-character alphanumeric `securityPickupCode = "K7X9"`, flags `allergyBadgePrinted = true`, and prints matching child/guardian tags.
3. Mid-service, classroom leader clicks **Page Guardian**; SMS/call prompt uses `Sarah Miller`'s `<rapider-phone-input>` number without printing her phone on the public name badge.
4. At pickup, `checkin-drawer` requires entering `"K7X9"` and selecting an authorized guardian from `authorizedPickupContactIds`; if `"K7X9"` mismatches or a restricted person attempts pickup, checkout is hard-blocked (`INCIDENT_HOLD`), whereas a verified lost-receipt guardian requires a Children's Director Home `WorkItem` photo-ID override.

### Journey 2: Worship Service Planning & Background-Check-Guarded Volunteer Scheduling
1. Worship Director creates `IndServicePlan` (`SRV-2026-1018`, Sunday 09:30 & 11:00) on `#/service-plans` with timed liturgy/song cues and opens `#/volunteer-rosters`.
2. Attempting to assign volunteer `Daniel Cho` (`backgroundCheckStatus = EXPIRED`) to `KIDS_YOUTH` Elementary Lead is deterministically blocked by `ind.church.assignVolunteer` with an actionable renewal prompt, whereas assigning cleared volunteer `Rachel Green` (`CLEARED`) succeeds while respecting her block-out dates.

### Journey 3: Clergy-Privileged Pastoral Care & Benevolence Utility Aid Handoff
1. Senior Pastor logs `IndPastoralCareCase` (`CARE-0312`, `CLERGY_CONFIDENTIAL`) for a congregant facing sudden job loss and bereavement, requesting `\$650.00` direct electric-utility benevolence assistance.
2. Submitting the benevolence request creates a Rapider Home `WorkItem` for the Benevolence/Finance Treasurer containing *only* case reference `CARE-0312`, payee utility `CrmAccount`, and `\$650.00` (`Decimal128`) — zero pastoral counseling notes are exposed.
3. Upon approval, a canonical `FinSupplierBill` is generated in `accpayable` payable directly to the utility provider.

### Journey 4: Dual-Custody Plate & Envelope Counting -> `#188` & `acc` Handoff
1. After Sunday services, Usher Counter A opens `giving-batch-drawer` (`BAT-2026-42`), logs `\$1,420.00` loose plate cash plus 38 numbered tithe envelopes (`\$8,580.00`, `countedTotalAmount = \$10,000.00`), and clicks **Submit for Second Verifier** (`PENDING_SECOND_VERIFIER`).
2. If Counter A tries to click **Verify & Lock** under the same user account, the server rejects self-verification (`primaryCounterUserId == secondaryVerifierUserId`).
3. Counter B independently recounts, confirms `\$10,000.00`, and signs off (`VERIFIED_LOCKED`), automatically syncing attributed envelope gifts to `#188` (`IndGiftTransaction` for year-end `IndTaxReceipt` statements) and posting a balanced `FinJournalEntry` to `acc`.

### Journey 5: Record Click-Through Navigation (`People & Households -> Household 360 -> Back Restoration`)
1. From `#/congregants` filtered to `Assimilation Stage: "FIRST_VISIT"` and `Search: "Miller"`, the Connections Coordinator clicks `Sarah Miller`.
2. Router navigates cleanly to `#/congregant-detail?id=00000000-0189-0000-0000-000000000105` without `<base href>` 404 diversion, rendering household members, group enrollments, and serving history (while hiding `CLERGY_CONFIDENTIAL` care cases and dollar giving totals from the Coordinator role).
3. Clicking `Back to list` (`#btnGoBack`) returns to `#/congregants` with `Assimilation Stage: "FIRST_VISIT"` and `Search: "Miller"` preserved in `#activeFilterTagsBar`.

---

## 6. Consolidated Feature Priorities & Work Packages

### `P0` Foundation Work Packages (Must-Have for Initial Release)
- **WP-P0-1 — Households, Assimilation Kanban & Small Groups (`CHM-001`, `CHM-002`, `CHM-003`):** Deliver `IndCongregantProfile` bound to `CrmContact`/`CrmAccount` with `<rapider-phone-input>`, `<rapider-kanban>` newcomer assimilation board, and `IndMinistryGroup` cohorts.
- **WP-P0-2 — Child Check-In Safety Codes, Ratios & Youth Background Gate (`CHM-006`, `CHM-007`, `CHM-008`, `CHM-021`):** Build `IndChildCheckInSession` cryptographic security pickup codes, allergy/custody alerts, parent paging, and hard background-check locks on youth `IndVolunteerAssignment`s.
- **WP-P0-3 — Worship Service Builder & Volunteer Rosters (`CHM-009`, `CHM-010`):** Deliver `IndServicePlan` run-of-show cues and `IndVolunteerAssignment` scheduling with block-out and family-together rules.
- **WP-P0-4 — Confidential Pastoral Care Vault & Dual-Custody Giving Batches (`CHM-013`, `CHM-014`):** Enforce server-side `CLERGY_CONFIDENTIAL` isolation on `IndPastoralCareCase` and two-verifier lock rules on `IndGivingBatch` with `#188`/`acc` handoffs.

### `P1` Enterprise Scale Work Packages
- **WP-P1-1 — Sacramental Registries, Opt-In Directory, CCLI & Campus Rooms (`CHM-004`, `CHM-005`, `CHM-011`, `CHM-012`):** Add multi-tradition `IndSacramentRecord` certificates, opt-in directory privacy, CCLI song reporting, and `HrLocation`/`OpsOperationsAsset` conflict prevention.
- **WP-P1-2 — Benevolence Aid, Pastor-Give Separation, Loose-Plate & Burnout Metrics (`CHM-015`, `CHM-016`, `CHM-017`, `CHM-022`):** Add redacted benevolence Home `WorkItem` -> `FinSupplierBill` payouts, clergy dollar-amount masking, envelope/loose-cash accounting, and >6-week volunteer burnout alerts.

### `P2` Adjacent & Grounded AI Work Packages
- **WP-P2-1 — Yahrzeit Reminders, Roster AI, Check-In Subs & GDPR Art. 9 (`CHM-018`, `CHM-019`, `CHM-020`, `CHM-023`, `CHM-024`):** Deliver annual Yahrzeit/milestone reminders, AI volunteer schedule optimization in `projectChannelMessage`, pastoral-safe assimilation copilot queries, live campus volunteer check-in, and GDPR Art. 9 erasure workflows.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **Ordained Clergy / Pastor / Rabbi / Imam** | Access and author `CLERGY_CONFIDENTIAL` & `CARE_TEAM_RESTRICTED` `IndPastoralCareCase`s, certify `IndSacramentRecord`s, lead `IndServicePlan`s. | By default (configurable anti-bias policy), sees congregant *"Active Giver"* badge rather than exact dollar gift amounts; cannot self-verify cash `IndGivingBatch`es. |
| **Children's / Youth Safety Director** | Manage `IndChildCheckInSession` classrooms, monitor ratios & allergies, verify `backgroundCheckStatus`, approve lost-tag pickup Home `WorkItem`s. | Zero access to `CLERGY_CONFIDENTIAL` counseling notes or congregant tithe/offering dollar records. |
| **Worship / Ministry Coordinator** | Build `IndServicePlan`s, schedule `IndVolunteerAssignment`s, manage `IndMinistryGroup`s and newcomer `<rapider-kanban>`. | Cannot schedule unscreened volunteers into youth roles; zero access to pastoral care vaults or giving batches. |
| **Offering Counter / Finance Steward** | Count or second-verify `IndGivingBatch`es, reconcile envelope numbers, trigger `#188` & `FinJournalEntry` postings, process approved benevolence `FinSupplierBill`s. | Cannot act as both primary counter and secondary verifier on the same batch; zero access to `IndPastoralCareCase` counseling narratives. |
| **Congregant / Volunteer (Self-Service)** | View own household, update block-out dates, accept/swap `IndVolunteerAssignment`s, view opt-in directory (`directoryOptIn = true` adults only). | Cannot view non-opted-in members, minor profiles outside own household, other families' pickup codes, pastoral logs, or giving batches. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### 8.1 Guarded Domain Commands
Every mutating endpoint enforces `idempotencyKey`, `correlationId`, and `expectedVersion`:
- `ind.church.checkInChild` / `ind.church.verifyChildPickup` — Generates unique `securityPickupCode`; blocks checkout unless code + authorized guardian match (or approved supervisor `WorkItem` override) and blocks `restrictedCustodyBlockNames`.
- `ind.church.assignVolunteer` — Checks block-out dates, room conflicts, and enforces `backgroundCheckStatus == CLEARED` (valid through `scheduledStartAt`) for all `KIDS_YOUTH` / `requiresBackgroundClearance` roles.
- `ind.church.verifyAndLockGivingBatch` — Enforces `primaryCounterUserId != secondaryVerifierUserId` and `countedTotalAmount == expectedControlTotal` (`Decimal128`), emitting gift/GL sync events.
- `ind.church.requestBenevolenceDisbursement` — Publishes a redacted Home `WorkItem` stripping `confidentialSummary` before routing to Finance.

### 8.2 Domain Events Published & Consumed (Kafka)
- **Published:** `ind.church.childCheckedIn.v1`, `ind.church.childPickupAlerted.v1`, `ind.church.givingBatchVerified.v1` (consumed by `#188` and `acc`), `ind.church.benevolenceApproved.v1` (consumed by `accpayable`).
- **Consumed:** `fin.payment.succeeded.v1` (links online weekend tithes), `mkt.event.created.v1` (syncs campus room reservations).

### 8.3 `requiredWorkflows` (Declared in `app.manifest.json`)
1. `childSafetyCheckInAndPagingWorkflow` — Enforces room ratios, generates non-colliding security pickup codes, dispatches guardian emergency SMS pages, and routes lost-tag overrides to Home `WorkItem`s.
2. `volunteerBackgroundExpiryAndBurnoutWorkflow` — Daily sweep expiring `IndCongregantProfile.backgroundCheckStatus` past `backgroundCheckExpiresAt`, auto-flagging affected upcoming youth shifts, and calculating consecutive-week burnout streaks.
3. `dualCustodyGivingToFundraisingAndGlWorkflow` — Converts `VERIFIED_LOCKED` `IndGivingBatch` envelope lines into `#188` `IndGiftTransaction`s and balanced `FinJournalEntry` postings.
4. `sacramentAndYahrzeitAnniversaryWorkflow` — Dispatches annual Yahrzeit/memorial and milestone pastoral care reminders.

### 8.4 Grounded Rapider AI Rules
- AI Volunteer Roster Suggestions (`CHM-019`) and Assimilation Copilot answers (`CHM-020`) MUST cite `IndCongregantProfile`, `IndMinistryGroup`, and `IndVolunteerAssignment` records.
- **Hard Privacy Wall:** `IndPastoralCareCase` (`CLERGY_CONFIDENTIAL`) and minor medical/custody fields MUST NEVER be indexed into shared workspace RAG prompts or surfaced by AI to non-authorized callers; AI MUST require human confirmation before publishing volunteer rosters or sending congregant communications.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **GDPR Article 9 (Special Category Religious Belief Data), COPPA & Clergy-Penitent Privilege:** Religious affiliation and sacramental records require explicit lawful basis / `gdprArt9ConsentAt`; minor profiles enforce guardian-only visibility; `CLERGY_CONFIDENTIAL` pastoral notes use field-level encryption at rest and strict RBAC row-level filtering.
- **Child Safeguarding & Permanence of Registers:** Child check-in/out logs (`IndChildCheckInSession`) and volunteer screening audit trails are retained immutably per child-protection insurance mandates; locked `IndSacramentRecord` registers are append-only historical archives.
- **Dual-Custody Monetary Precision:** All cash, check, and envelope offering counts (e.g., `\$10,000.00` weekend batch) and benevolence payouts (`\$650.00`) use `Decimal128`.
- **Accessibility & Kiosk/Mobile UX:** Full WCAG 2.2 AA compliance (`#ffffff !important` contrast on primary/danger buttons across light and dark modes, ARIA labels on icon-only Delete buttons) across `390px` volunteer phones, `768px` foyer check-in iPads/kiosks, and `1440px` church office desktops.

---

## 10. Deterministic Acceptance Criteria

1. **Sidebar 3-Item Section Rule:** `app.manifest.json` defines 3 visible sidebar sections (`Overview`, `Ministry & Youth Safety`, `Care, Rites & Stewardship`) with 3 visible items each (`displayOnMenu: true`) and 4 hidden detail/drawer routes (`displayOnMenu: false`).
2. **SWR & Soft-Delete Cleanliness:** Every page load uses `findSWR` / `countSWR` without manual `isDeleted` API query filters and defensively filters `item.isDeleted !== true` in memory.
3. **Active Filter Tags & Clear All:** Filtering `#/congregants`, `#/assimilation-groups`, or `#/volunteer-rosters` renders `#activeFilterTagsBar` with HTML-escaped dismissible chips and `[Clear all]`, synchronously updating table and `<rapider-kanban>` views.
4. **Table Action Standard:** Zero standalone "View" buttons exist in `Actions`; Member Names, Service Titles, Check-In Codes, Certificate Numbers, and Batch Numbers navigate to detail routes, Edit buttons render icon + text, and Delete buttons render icon-only with `title="Delete"` and `aria-label="Delete"`.
5. **Custom Elements Adoption:** Guardian paging and congregant phone inputs use `<rapider-phone-input>`, and `#/assimilation-groups` uses `<rapider-kanban>`.
6. **Optimistic Lifecycle & Native Dialog Ban:** Saving `checkin-drawer` or `giving-batch-drawer` resets button state in `finally`, calls `closePageDrawer()`, clears SWR cache, and updates parent views optimistically; deletions use `#rapiderConfirmOkBtn` with zero `window.alert`/`confirm`/`prompt`.
7. **Cryptographic Child Pickup & Custody Gate:** Attempting `ind.church.verifyChildPickup` with a mismatched `securityPickupCode` or an unauthorized guardian not in `authorizedPickupContactIds` fails deterministically unless an approved supervisor Home `WorkItem` override is linked.
8. **Youth Background-Check Hard Block:** Assigning a volunteer with `backgroundCheckStatus != CLEARED` (or expiring before service start) to a `KIDS_YOUTH` `IndVolunteerAssignment` is deterministically rejected.
9. **Dual-Custody Offering Verification:** Attempting to lock an `IndGivingBatch` where `secondaryVerifierUserId == primaryCounterUserId` or `countedTotalAmount != expectedControlTotal` fails deterministically.
10. **Clergy-Privileged Pastoral Isolation:** Querying `IndPastoralCareCase` (`CLERGY_CONFIDENTIAL`) as a Finance Steward, Youth Director, or Volunteer Coordinator returns zero records, and benevolence Home `WorkItem`s omit `confidentialSummary`.
11. **Click-Through Navigation & State Restoration:** Clicking a congregant on `#/congregants` transitions to `#/congregant-detail?id=...` without `<base href>` 404 diversion, renders household and serving history, and `Back to list` restores prior filter tags.
12. **Canonical Suite Reuse & Zero `projectId`:** Zero `Ind*` schemas define `projectId`, and households, online payments, tax receipts, vendor payouts, and GL journals reuse `CrmAccount`/`CrmContact`, `FinPaymentIntent`, `#188`, `FinSupplierBill`, and `FinJournalEntry`.

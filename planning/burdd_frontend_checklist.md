# ✅ **Burdd Frontend Build Checklist**

_Stack: React 18 • TypeScript 5 • Vite 5 • CSS Modules • React Router 6_  
_Data: local mock JSONs → replace with real API later_  
_Quality: ESLint + Prettier + Vitest + React Testing Library_

---

## **🗓️ Day 1 — Repo & Tooling Bootstrap**

**Goal:** Initialize environment, enforce lint + style consistency.

- [ ] Create `frontend/` repo with Vite (React + TS template)  
- [ ] Enable `strict` mode in `tsconfig.json`  
- [ ] Set up CSS Modules & import sample `.module.css`  
- [ ] Install ESLint (React/TS) + Prettier + EditorConfig  
- [ ] Add pre-commit hook (`lint-staged`, `husky`)  
- [ ] Create `src/styles/globals.css` and `variables.css`  
- [ ] Verify `npm run dev`, `npm run lint`, `npm run test` all succeed  
- [ ] Commit baseline and push to main

---

## **🗓️ Day 2 — Routing & Layout**

**Goal:** Set up global layout + page routing.

- [ ] Install React Router v6  
- [ ] Define base routes:  
  - [ ] `/login`  
  - [ ] `/projects`  
  - [ ] `/projects/:id`  
  - [ ] `/sprints/:id`  
  - [ ] `/issues/:id`  
  - [ ] `/tickets/new`  
  - [ ] `/tickets/triage`  
- [ ] Build `AppLayout` with header + sidebar navigation  
- [ ] Add responsive CSS Grid + active-link styles  
- [ ] Implement 404 Not Found route  
- [ ] Validate deep links refresh without crash  
- [ ] Verify keyboard navigation and ARIA roles

---

## **🗓️ Day 3 — Mock API Layer & Fetch Helpers**

**Goal:** Introduce local data mocks and typed fetch utilities.

- [ ] Add `mock-api/projects.json`, `sprints.json`, `issues.json`, `tickets.json`  
- [ ] Create `src/lib/fetcher.ts` with typed helpers  
  - [ ] `getList<T>(endpoint)`  
  - [ ] `getById<T>(endpoint, id)`  
- [ ] Implement `ApiProvider` context for data source swapping  
- [ ] Wire example page fetching project list  
- [ ] Confirm types flow end-to-end (`Project`, `Issue`, `Ticket`)  
- [ ] Inspect mock fetches in browser Network tab

---

## **🗓️ Day 4 — Projects List & Details**

**Goal:** Build project management views.

- [ ] Create `/projects` list page  
  - [ ] Fetch all projects  
  - [ ] Text-filter by name  
  - [ ] Empty-state message  
- [ ] Create `/projects/:id` detail page  
  - [ ] Show name, description, members, active sprint, issues summary  
  - [ ] Fetch related sprints + issues  
- [ ] Reusable UI:  
  - [ ] `DataTable`  
  - [ ] `Tag`  
  - [ ] `EmptyState`  
- [ ] Style both pages with CSS Modules  
- [ ] Verify instant filtering and navigation to detail view

---

## **🗓️ Day 5 — Sprint Board**

**Goal:** Implement kanban-style board view.

- [ ] Create `/sprints/:id` route with sprint summary  
- [ ] Columns: **In Queue**, **In Progress**, **Code Review**, **Done**  
- [ ] Render issues grouped by status  
- [ ] Add drag-and-drop (basic, no persistence yet)  
- [ ] Add keyboard “Move to Column” menu for accessibility  
- [ ] Display column totals and empty state  
- [ ] Test DnD and keyboard navigation  
- [ ] Confirm ARIA labels announce movement

---

## **🗓️ Day 6 — Issue Details & Comments**

**Goal:** Detailed issue tracking + threaded discussion.

- [ ] Build `/issues/:id` view  
  - [ ] Title, status, assignee, description, linked tickets  
- [ ] Create comments thread  
  - [ ] Optimistic add (local state)  
  - [ ] Error display on failure  
- [ ] Create `FormField` components (label/help/error)  
- [ ] Validate fields and UX consistency  
- [ ] Ensure immediate UI update on new comment

---

## **🗓️ Day 7 — Public Ticket Intake**

**Goal:** Public ticket submission flow (no auth).

- [ ] Build `/tickets/new` form  
  - [ ] Title, description, email opt-in  
  - [ ] File input (mock upload)  
- [ ] Validate required fields  
- [ ] On submit, generate tokenized status link  
- [ ] Show success screen with link copy button  
- [ ] Focus management for error/success states  
- [ ] Verify keyboard accessibility and responsive layout

---

## **🗓️ Day 8 — Ticket Triage (Developer)**

**Goal:** Developer triage queue with convert/link flows.

- [ ] Build `/tickets/triage` list view  
  - [ ] Filter: new / linked / converted  
- [ ] Add action buttons:  
  - [ ] “Convert to Issue” → creates new mock issue and removes from queue  
  - [ ] “Link to Issue” → opens modal with search and selection  
- [ ] Implement modal UI and toasts  
- [ ] Update mock data after action  
- [ ] Verify success/error feedback flows

---

## **🗓️ Day 9 — Auth Shell & Protected Routes**

**Goal:** Minimal authentication mock for developer/admin flows.

- [ ] Create `AuthProvider` context (`login`, `logout`, `user`)  
- [ ] `/login` page form with error state  
- [ ] Guard routes → redirect unauthenticated users to `/login`  
- [ ] Show logged-in user and logout button in header  
- [ ] Restrict public access to only `/login` and `/tickets/new`  
- [ ] Verify redirects and protected routes behavior

---

## **🗓️ Day 10 — Styling Polish & Responsiveness**

**Goal:** Final UI refinement and a11y pass.

- [ ] Define global typography scale + spacing variables  
- [ ] Add responsive breakpoints for tables and boards  
- [ ] Compact cards on mobile view  
- [ ] Implement loading/error/empty skeletons  
- [ ] Test scroll behavior on mobile board  
- [ ] Run Lighthouse → a11y ≥ 90, contrast passes  
- [ ] Verify tab order and focus states are logical

---

## **🗓️ Day 11 — Testing & Error Boundaries**

**Goal:** Strengthen reliability and type safety.

- [ ] Add Vitest + React Testing Library  
- [ ] Write unit tests for key components (15–25 total)  
- [ ] Add page-level happy path tests  
- [ ] Strengthen types with discriminated unions for load states  
- [ ] Create `ErrorBoundary` and `NotFoundBoundary`  
- [ ] Verify CI runs `lint` + `test` + `build`  
- [ ] Ensure type-only errors fail CI

---

## **🗓️ Day 12 — Packaging & Docs**

**Goal:** Prep for release and handoff.

- [ ] Add build script (`npm run build`) with `VITE_API_BASE` env  
- [ ] Verify `dist/` serves mock data correctly  
- [ ] Create `README_frontend.md` with setup + run instructions  
- [ ] Add page map + env variable docs  
- [ ] Write handoff notes for real API integration  
- [ ] Add CHANGELOG entry for v1.0 frontend MVP  
- [ ] Confirm final preview works end-to-end

---

## **📋 Daily Definition of Done**

- [ ] Lint clean  
- [ ] Strict types (no `any`)  
- [ ] 1–2 tests for new components  
- [ ] Keyboard + screen-reader accessible  
- [ ] Mock JSON updated if schema changed  

---

# 🚀 Public Feedback Portal Checklist

This checklist covers the features needed for the public-facing social media-style interface, which allows users to submit feedback and track its progress.

## 🏛️ Core Pages & Views

- [ ] **Feedback Dashboard (Homepage)**
  - Displays a list/feed of all public submissions.
  - Primary "Submit New Idea" CTA button.

- [ ] **Feedback Detail Page**
  - Shows the full details for a single submission.
  - Contains the upvote button, status, and comment thread.

- [ ] **Submission Form Page**
  - A dedicated page with the form to submit new feedback.

- [ ] **Submission Success Page**
  - A confirmation screen shown after submitting.
  - Displays the unique "tracking link" for the user to "revisit" their ticket (avoids public-user auth).

## 🔁 Key Features & Functionality

- [ ] **Feedback List & Filtering**
  - Render each submission as a "card" in the list.
  - Display essential info on the card: Title, Upvote Count, Comment Count, Category Tag, and Status Badge.
  - **Filter controls:**
    - [ ] Filter by Category (Feature, Issue, Suggestion)
    - [ ] Filter by Status (Under Review, In Progress, Shipped)
  - **Sort controls:**
    - [ ] Sort by "Hot" / "Trending" (Upvotes + recent activity)
    - [ ] Sort by "Top" (Most upvotes)
    - [ ] Sort by "Newest"

- [ ] **Submission Form**
  - Title field (text input)
  - Category field (dropdown/radio: Feature, Issue, Suggestion)
  - Description field (textarea, ideally supporting simple Markdown)
  - (Optional) Field for attachments/screenshots
  - Client-side validation for required fields

- [ ] **User Interaction**
  - **Upvoting:** A button on both the list card and the detail page that increments a counter (one vote per user/session)
  - **Commenting:**
    - [ ] A "post a comment" form on the detail page
    - [ ] A read-only list displaying all comments for that submission

- [ ] **Status Tracking (The link to the Dev side)**
  - Display the submission's current status (e.g., "Backlog," "In Progress," "Completed") as a visual badge
  - This status is read-only for the public and is set by the dev team (from the Burdd app)

## 🧩 Reusable UI Components

- [ ] **FeedbackCard:** The item used in the main dashboard list
- [ ] **UpvoteButton:** A stateful component showing count and clicked/un-clicked state
- [ ] **StatusBadge:** A simple tag with different colors based on the status prop (e.g., blue for "In Progress," green for "Shipped")
- [ ] **CategoryTag:** A tag for "Feature," "Issue," etc.
- [ ] **CommentThread:** Container that lists all Comment components
- [ ] **Comment:** A simple component to display a comment's text and author/date

## **🚀 Pre-Release Checklist**

- [ ] Local build verified (`npm run build`)  
- [ ] README and routes accurate  
- [ ] Known Gaps section lists API integration points  
- [ ] Demo preview confirmed functional  

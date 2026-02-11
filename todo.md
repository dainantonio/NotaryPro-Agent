# NotaryOS Premium UI Refactor - Task List

## Phase 1: Inventory & Map
- [ ] Analyze existing UI patterns (buttons, inputs, tables, cards, nav, modals, toasts)
- [ ] Document current component usage and locations
- [ ] Identify all screens that need migration

## Phase 2: Design Tokens
- [x] Implement CSS variables for spacing, typography, colors, radii, shadows
- [x] Update :root styles in index.html
- [x] Test token application without layout changes
- [x] Create DESIGN_TOKENS_IMPLEMENTATION.md documentation

## Phase 3: Shared Component Library
- [ ] Create Button component with variants (primary, secondary, ghost, danger)
- [ ] Create Input/Select/Textarea components
- [ ] Create Card component
- [ ] Create Table component with hover states
- [ ] Create Badge component
- [ ] Create Modal/Drawer wrapper
- [ ] Update Toast/Alert styles
- [ ] Create Skeleton loader
- [ ] Create EmptyState template

## Phase 4: Incremental Migration
- [ ] Migrate Global Navigation (Header + SideNav)
- [ ] Migrate Dashboard
- [ ] Migrate Appointments/Schedule
- [ ] Migrate Notary Journal
- [ ] Migrate Clients
- [ ] Migrate Expenses
- [ ] Migrate Settings
- [ ] Migrate Auth screens (Login/Signup)

## Phase 5: QA & Regression
- [ ] Create regression checklist
- [ ] Create smoke test steps
- [ ] Verify all flows still work
- [ ] Document changes

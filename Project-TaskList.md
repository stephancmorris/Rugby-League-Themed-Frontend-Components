# NRL Component Library - 3-Day MVP Task List

**Project Goal**: Create a production-ready React component library showcasing skills for NRL Full Stack Engineer - Front End role

**Target Role Skills**:
- ✅ React.js & Next.js
- ✅ TypeScript & Modern JavaScript
- ✅ Well-tested, accessible components
- ✅ API integration patterns
- ✅ Performance optimization
- ✅ Modern frontend architecture

---

## 📊 Kanban Board

### 🔵 TODO - Day 1 Morning (3-4 hours)

#### **Epic: Foundation & Infrastructure**

- [ ] **Initialize Project** (30 min)
  - Create React + TypeScript + Vite project
  - Configure `tsconfig.json` with strict mode
  - Setup `package.json` with proper metadata
  - **Acceptance**: `npm run dev` works, TypeScript strict mode enabled

- [ ] **Install Core Dependencies** (15 min)
  - React 18.2+, TypeScript 5.0+
  - @emotion/react, @emotion/styled
  - **Acceptance**: All dependencies installed, no conflicts

- [ ] **Setup Storybook 7** (30 min)
  - Install Storybook with Vite builder
  - Configure for React + TypeScript + Emotion
  - Add essential addons (controls, actions, a11y)
  - **Acceptance**: `npm run storybook` launches successfully

- [ ] **Create Project Structure** (15 min)
  ```
  src/
  ├── components/
  │   ├── Button/
  │   ├── Card/
  │   ├── Badge/
  │   └── MatchCard/
  ├── theme/
  ├── types/
  └── hooks/
  ```
  - **Acceptance**: All folders created, index files in place

- [ ] **Design Token System** (45 min)
  - Create `src/theme/tokens.ts` with colors, spacing, typography
  - Define 5 team color palettes:
    - Warriors (blue/green)
    - Dragons (red/white)
    - Roosters (navy/red/white)
    - Perth Bears (black/gold)
    - PNG Chiefs (red/yellow/black)
  - **Acceptance**: Tokens exported, teams have primary/secondary colors

- [ ] **ThemeProvider Component** (45 min)
  - Create `src/theme/ThemeProvider.tsx`
  - Emotion ThemeProvider wrapper
  - Context for current team theme
  - `useTheme()` custom hook
  - **Acceptance**: Components can access theme via hook

- [ ] **TypeScript Type Definitions** (30 min)
  - `src/types/index.ts` with:
    - `Team` interface (id, name, colors, logo)
    - `Match` interface (id, teams, scores, status, venue, date)
    - `MatchStatus` type ('upcoming' | 'live' | 'completed')
  - **Acceptance**: Types exported and importable

---

### 🟡 IN PROGRESS - Day 1 Afternoon (4 hours)

#### **Epic: Core UI Components**

- [ ] **Button Component** (45 min)
  - `src/components/Button/Button.tsx`
  - Variants: `primary`, `secondary`, `ghost`
  - Sizes: `sm`, `md`, `lg`
  - Props: `loading`, `disabled`, `icon`, `fullWidth`
  - Emotion styled components
  - **Acceptance**:
    - All variants render correctly
    - TypeScript props interface complete
    - Accessible (keyboard, ARIA)

- [ ] **Button Storybook Stories** (15 min)
  - `Button.stories.tsx` with all variants
  - Interactive controls for props
  - **Acceptance**: All variants visible in Storybook

- [ ] **Card Component** (45 min)
  - `src/components/Card/Card.tsx`
  - Props: `elevation`, `padding`, `bordered`
  - Slots: `header`, `body`, `footer` (using children composition)
  - **Acceptance**:
    - Renders with shadow/border styles
    - Flexible content composition
    - TypeScript props complete

- [ ] **Card Storybook Stories** (15 min)
  - `Card.stories.tsx` with examples
  - Show different elevation levels
  - **Acceptance**: Card variants in Storybook

- [ ] **Badge Component** (30 min)
  - `src/components/Badge/Badge.tsx`
  - Variants: `team`, `status`, `info`
  - Props: `color`, `size`, `rounded`
  - **Acceptance**:
    - Renders with team colors
    - Status badges (live, upcoming, completed)
    - TypeScript complete

- [ ] **Badge Storybook Stories** (15 min)
  - `Badge.stories.tsx`
  - Show all 5 team colors
  - Show status variants
  - **Acceptance**: All badge types in Storybook

- [ ] **MatchCard Component - Part 1** (90 min)
  - `src/components/MatchCard/MatchCard.tsx`
  - Props based on `Match` interface
  - Layout:
    - Home team (left) vs Away team (right)
    - Team badges with colors
    - Scores (if available)
    - Venue and date/time
    - Status indicator (live/upcoming/completed)
  - Use Button, Card, Badge components
  - Responsive design (mobile/desktop)
  - **Acceptance**:
    - Displays match information correctly
    - Team colors applied dynamically
    - All props typed
    - Responsive layout works

---

### 🟠 TESTING - Day 2 Morning (3 hours)

#### **Epic: MatchCard Polish & Testing Setup**

- [ ] **MatchCard Component - Part 2** (60 min)
  - Add all 5 team theme support
  - Create loading skeleton variant
  - Add action buttons (View Details, Share)
  - Polish spacing and typography
  - **Acceptance**:
    - All 5 team combinations look good
    - Loading state renders
    - Actions work (callback props)

- [ ] **MatchCard Storybook Stories** (45 min)
  - `MatchCard.stories.tsx` with comprehensive examples:
    - Story: Upcoming match
    - Story: Live match with scores
    - Story: Completed match
    - Story: Loading state
    - Story: All team combinations
  - Add Storybook controls for interactive testing
  - **Acceptance**: All MatchCard states documented

- [ ] **Install Testing Dependencies** (15 min)
  - Jest, @testing-library/react, @testing-library/jest-dom
  - @testing-library/user-event
  - jest-axe (accessibility testing)
  - @types/jest
  - **Acceptance**: `npm test` command works

- [ ] **Configure Jest** (30 min)
  - Create `jest.config.js`
  - Setup test environment (jsdom)
  - Configure Emotion for tests
  - Create `src/test-utils.tsx` with custom render
  - **Acceptance**: Test suite runs without errors

- [ ] **Write Button Tests** (30 min)
  - `Button.test.tsx`:
    - Renders with text
    - Handles click events
    - Shows loading state
    - Disabled state works
    - Accessibility test with jest-axe
  - **Acceptance**: All tests pass, >90% coverage

- [ ] **Write MatchCard Tests** (60 min)
  - `MatchCard.test.tsx`:
    - Renders match information correctly
    - Displays team names and scores
    - Shows correct status badge
    - Handles missing data gracefully
    - Callback props work
    - Accessibility test with jest-axe
  - **Acceptance**: All tests pass, >85% coverage

---

### 🟢 DONE - Day 2 Afternoon & Day 3 (5 hours)

#### **Epic: API Integration & Next.js Demo**

- [ ] **Setup Mock Service Worker (MSW)** (45 min)
  - Install `msw` dependency
  - Create `src/mocks/handlers.ts`:
    - `GET /api/matches` - returns array of matches
    - `GET /api/matches/:id` - returns single match
    - `GET /api/teams` - returns all teams
    - `GET /api/ladder` - returns ladder standings
  - Create `src/mocks/data.ts` with realistic NRL data
  - Setup MSW for Storybook
  - **Acceptance**:
    - Handlers return typed responses
    - Mock data includes all 5 teams
    - MSW works in Storybook

- [ ] **Create Data Fetching Hooks** (60 min)
  - Install `@tanstack/react-query`
  - Create `src/hooks/useMatches.ts`:
    - Fetches from `/api/matches`
    - Returns loading, error, data states
    - TypeScript types for responses
  - Create `src/hooks/useMatchById.ts`
  - **Acceptance**:
    - Hooks return proper loading/error/data
    - Type-safe responses
    - Works with MSW

- [ ] **Update MatchCard for Real Data** (30 min)
  - Create `MatchCardContainer` that uses `useMatchById`
  - Show loading skeleton while fetching
  - Handle error states
  - **Acceptance**: MatchCard works with async data

- [ ] **Accessibility Enhancements** (45 min)
  - Add keyboard navigation to MatchCard
  - Proper ARIA labels on all interactive elements
  - Focus management
  - Screen reader text for scores ("Home team 24, Away team 18")
  - **Acceptance**:
    - Tab navigation works
    - Screen reader announces content
    - No axe violations

- [ ] **Initialize Next.js Demo App** (30 min)
  - Create separate `demo/` folder with Next.js 14+
  - Install Next.js with TypeScript
  - Setup Tailwind CSS (or use Emotion)
  - **Acceptance**: `npm run dev` works in demo folder

- [ ] **Setup Component Library in Next.js** (30 min)
  - Configure demo app to import from `../src`
  - Or publish locally and install via npm link
  - Setup MSW in Next.js
  - **Acceptance**: Can import components in Next.js

- [ ] **Create Match Listing Page** (60 min)
  - `demo/app/page.tsx` - Homepage with match list
  - Use `useMatches()` hook
  - Server-side render with Next.js App Router
  - Grid of MatchCard components
  - **Acceptance**:
    - SSR works (view source shows content)
    - Matches display correctly
    - Responsive layout

- [ ] **Create Match Detail Page** (45 min)
  - `demo/app/matches/[id]/page.tsx`
  - Use `useMatchById()` hook
  - Static params generation for all matches
  - Show detailed match information
  - **Acceptance**:
    - Dynamic routes work
    - SSG generates pages
    - Match details display

- [ ] **Performance Optimization** (30 min)
  - Add React.memo to MatchCard
  - Lazy load non-critical components
  - Optimize images (if any)
  - Add loading states
  - **Acceptance**: Lighthouse score >90

---

### 📦 Final Polish & Documentation (Day 3 - Final 2 hours)

#### **Epic: Documentation & Package Preparation**

- [ ] **Create Comprehensive README** (45 min)
  ```markdown
  # NRL Component Library

  ## Features
  - 5 production-ready components
  - 5 NRL team themes
  - TypeScript support
  - Storybook documentation
  - Tested & accessible

  ## Installation
  ## Usage Examples
  ## API Documentation
  ## Development
  ## Testing
  ```
  - **Acceptance**: Clear, professional README

- [ ] **Package.json Configuration** (30 min)
  - Set proper exports (`main`, `module`, `types`)
  - Configure peer dependencies
  - Add scripts (dev, build, test, storybook)
  - Set version to `0.1.0`
  - **Acceptance**: Package ready for publishing

- [ ] **Build Configuration** (30 min)
  - Configure Vite for library mode
  - Generate TypeScript declarations
  - Test build output
  - **Acceptance**: `npm run build` produces dist folder

- [ ] **Deploy Storybook** (15 min)
  - Build Storybook static site
  - Deploy to Vercel/Netlify/Chromatic
  - Get public URL
  - **Acceptance**: Live Storybook link works

- [ ] **Deploy Next.js Demo** (15 min)
  - Deploy demo app to Vercel
  - Configure environment for MSW
  - Get public URL
  - **Acceptance**: Live demo link works

- [ ] **Final QA Checklist** (30 min)
  - [ ] All components render in Storybook
  - [ ] All tests pass
  - [ ] No console errors
  - [ ] Accessibility: No axe violations
  - [ ] All 5 team themes work
  - [ ] Next.js demo works
  - [ ] Build succeeds
  - [ ] TypeScript compiles with no errors
  - [ ] README is complete
  - **Acceptance**: All items checked

- [ ] **Create Project Summary** (15 min)
  - Document architecture decisions
  - List technologies used
  - Add screenshots
  - Create demo GIF/video (optional)
  - **Acceptance**: Portfolio-ready documentation

---

## 🎯 Success Metrics

### Technical Deliverables
- ✅ **5 Components**: Button, Card, Badge, MatchCard, ThemeProvider
- ✅ **5 Team Themes**: Working color system
- ✅ **Storybook**: Interactive documentation
- ✅ **Tests**: Jest + RTL + jest-axe
- ✅ **MSW**: Mock API integration
- ✅ **Next.js**: SSR/SSG demo app
- ✅ **TypeScript**: 100% typed
- ✅ **Accessible**: WCAG 2.1 AA patterns

### Role Alignment
| Requirement | Demonstrated By |
|------------|----------------|
| React.js & Next.js | Component library + Next.js demo |
| Well-tested components | Jest + RTL tests with >85% coverage |
| Accessible interfaces | ARIA labels, keyboard nav, axe tests |
| API integration | MSW handlers with React Query |
| TypeScript | Fully typed components and APIs |
| Modern patterns | Custom hooks, composition, SSR/SSG |
| Performance | React.memo, lazy loading, Lighthouse >90 |
| Code quality | Storybook docs, tests, clean structure |

---

## 📝 Notes

### Out of Scope (For MVP)
- ❌ Additional components beyond the 5 core
- ❌ Full 16-team theming
- ❌ Dark mode
- ❌ Real-time WebSocket updates
- ❌ Complex state management (Redux/Zustand)
- ❌ E2E tests (Playwright/Cypress)
- ❌ CI/CD pipeline
- ❌ NPM publishing

### Future Enhancements (Post-MVP)
- Add LeaderboardTable component
- PredictionForm with validation
- More team themes
- GraphQL API example
- OAuth integration example
- Microservices architecture demo

---

## 🚀 Getting Started

1. **Day 1**: Foundation + Core Components
2. **Day 2**: Testing + Polish
3. **Day 3**: Next.js + MSW + Deploy

**Estimated Total Time**: 18-20 hours over 3 days

---

## 📚 Resources

- [MSW Documentation](https://mswjs.io/)
- [React Query](https://tanstack.com/query/latest)
- [Storybook](https://storybook.js.org/)
- [React Testing Library](https://testing-library.com/react)
- [jest-axe](https://github.com/nickcolley/jest-axe)
- [Next.js App Router](https://nextjs.org/docs/app)

---

**Last Updated**: 2024-11-13
**Status**: Ready to Start
**Target Role**: NRL Full Stack Engineer - Front End

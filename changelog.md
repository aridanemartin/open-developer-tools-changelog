# Open Developer Tools: Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.7.0] - 2/1/2026 🚀

### Added

**Git Branch Generator Configuration**
- Added "Reset type of task and task prefix after copying the branch" option in Features tab
- When enabled, automatically resets the type of task and task prefix fields to their default values after copying the generated branch name
- Default value is unchecked (disabled)
- Added "None" option to command dropdown for copying branch names without git commands

**Quick Actions**
- Added "Quick Actions" section in Config → General tab
- Added "Refresh all Chrome tabs" button in secondary navigation strip
- Added "Zen mode" button in secondary navigation strip that closes all tabs except the current one
- Added confirmation dialogs for both quick actions (configurable in settings)
- Error handling when attempting Zen mode with only one tab open

### Changed

**Configuration Organization**
- Moved "Auto-scrape from task managers" setting from General tab to Features tab
- Added new "Git branch generator" section in Features tab to organize branch generation settings

**PostMessage Debugger UI**
- Updated PostMessage Debugger to use MuiTabs with same indicator styles as QuickCopy
- Replaced custom tab implementation with Material-UI Tabs component for consistency
- Removed "Send & Save" button from PostMessage form actions
- Repositioned Save button to the left and Send button to the right
- Added save icon to Save button for better visual clarity
- Both buttons now occupy equal space for balanced layout

**QuickCopy UI**
- Added + button next to search bar in QuickCopy tab for quick navigation to create item tab
- + button matches PostMessageDebugger functionality and styling
- Improved user experience with direct access to item creation

**Configuration UI**
- Updated Config component to use MuiTabs with same indicator styles as QuickCopy and PostMessage Debugger
- Replaced custom tab implementation with Material-UI Tabs component for consistency across all components

## [1.6.0] - 24/9/2025 🚀

### Changed

**Default Message Colors**
- Updated default GitHub Booster message colors to use a dark theme:
  - Background Color: `#011627` (dark blue)
  - Text Color: `#a7d9cf` (light teal)
  - Border Color: `#a7dacf` (light teal)

### Added

**Tab Management System**
- Added tab management functionality with hide/show capabilities.
- Users can now enable/disable individual tabs from the extension interface.
- Tab reordering functionality for customizing tab display order.

**Default Examples**
- Added default examples to QuickCopy tab with common code snippets and commands.
- Added default examples to PostMessageDebugger tab with typical postMessage scenarios.
- Examples include authentication, navigation, and data update patterns for better user onboarding.

**PostMessageDebugger Styling Improvements**
- Enhanced item description styling to match QuickCopy tab design consistency.
- Improved target origin text visibility with main font color styling.
- Added text truncation with ellipsis for long target origins (max-width: 350px).
- Enhanced visual hierarchy with better typography and spacing.
- Improved layout responsiveness for better user experience.

### Technical Implementation

**Tab System Refactoring**
- Refactored tab system to use semantic string identifiers instead of numeric values.
- Created `useTabManager` custom hook to extract complex tab logic from App component.
- Improved code maintainability by centralizing tab management logic.
- Enhanced tab system to be future-proof when adding or removing tabs.
- Updated all tab references to use semantic identifiers (`git-branch-generator`, `config`, etc.).
- Simplified tab structure by removing redundant `value` property, using only `id`.

**Playwright Test Organization**
- Reorganized Playwright tests by tab functionality for better maintainability.
- Created dedicated test folders for each tab: `GitBranchGenerator`, `QuickCopy`, `GitHubSearch`, `GithubBooster`, `PostMessageDebugger`, `Config`.
- Added generic app tests folder for cross-tab functionality tests.
- Updated test file naming from `task-branch.spec.ts` to `git-branch-generator.spec.ts` for consistency.
- Enhanced `ExtensionHelpers` with `navigateToTab()` method for easier tab-specific testing.
- Added comprehensive npm scripts for running tests by tab or functionality:
  - `npm run test:e2e:all` - Run all Playwright tests
  - `npm run test:e2e:app` - Run generic app tests
  - `npm run test:e2e:git-branch` - Run GitBranchGenerator tests
  - `npm run test:e2e:quick-copy` - Run QuickCopy tests
  - `npm run test:e2e:github-search` - Run GitHubSearch tests
  - `npm run test:e2e:github-booster` - Run GithubBooster tests
  - `npm run test:e2e:postmessage` - Run PostMessageDebugger tests
  - `npm run test:e2e:config` - Run Config tests
- Maintained backward compatibility by keeping `taskBranch` state property while using `git-branch-generator` for tab identification.
- Updated test data and validation to support the new organization structure.
- Added comprehensive documentation for the new test structure in `tests/e2e/specs/README.md`.

## [1.5.1] - 2025-09-21 🚀

### Added

**Config section**
- Added confirmation dialog for reset all settings.
- Split configuration into multiple tabs for better organization.

### Fixed

**QuickCopy section**
- Improved styled for quick copy items.
- Rename every deprecated code from QuickStore to QuickCopy.

**GitHub Booster section**

- PR title validation is now enabled by default for new users.
- Removed configuration from GitHub Booster section.
- Improved texts for better readability.
- Fixed PR validation not working when navigating to compare page and clicking "Create pull request" without page reload.
- Enhanced MutationObserver to better detect dynamically loaded PR forms with additional selectors.
- Added event listener for "Create pull request" button clicks to handle dynamic form loading.
- Implemented periodic check as fallback mechanism to ensure PR validation works on compare pages.
- Improved DOM change detection with better timing and more comprehensive selectors.

### Technical Implementation

- Added `setupCreatePRButtonListener()` method to catch button clicks and trigger validation setup.
- Enhanced MutationObserver with additional form selectors for better detection coverage.
- Implemented periodic check interval (1 second) specifically for compare pages as fallback.
- Added proper cleanup for new interval timer in destroy method.
- Used event delegation with capture phase for early event detection.

## [1.5.0] - Working on PostMessage Debugger 

### Added

**PostMessage Debugger section**

- Enhanced PostMessage events list with improved visual styling matching QuickCopyTab design.
- Applied consistent border, border-radius, and hover effects to PostMessage items.
- Improved favorite button styling with special orange/yellow filter when favorited.

## [1.4.1] - 2025-01-04 🚀

### Fixed

**Config section**

- Fixed download JSON functionality to include complete state data, ensuring all preferences fields are present in exported files.
- Improved upload JSON functionality with backward compatibility support for old preference files.
- Enhanced validation to handle partial state objects, allowing seamless imports from older versions.
- Updated error messages to provide clearer feedback during import/export operations.
- Fixed theme selection export to ensure `selectedColorTheme` and all nested configuration objects are properly included in JSON exports.
- Implemented deep merging for export functionality to prevent loss of nested object properties during state serialization.

### Technical Implementation

- Created `exportPreferences.ts` helper with complete state merging functionality.
- Created `importPreferences.ts` helper with recursive deep merge for backward compatibility.
- Improved JSON formatting in exported files with proper indentation for better readability.
- Enhanced error handling with more descriptive error messages.
- Configured Jest testing framework with TypeScript and ES modules support.
- Created comprehensive test suites for both import and export functionality with 37 passing tests.
- Added test scripts: `npm test`, `npm run test:watch`, `npm run test:coverage`, and `npm run test:ci`.
- Implemented DOM testing with jsdom environment for download functionality testing.
- Created `.cursorrules` file with test writing guidelines to avoid comments in test files.

## [1.4.0] - 2025-09-03 🚀

### Removed

- Release branch section temporarily removed to focus on the most important features.

### Added

**QuickCopy section**

- Added the ability to add items to the quick copy.
- Added the ability to remove items from the quick copy.
- Added the ability to search for items in the quick copy.
- Added the ability to add items to the quick copy.
- Added the ability to remove items from the quick copy.

**GitHub Search section**

- Added the ability to search for repositories by name.
- Added the ability to add repositories to favorites.
- Added the ability to remove repositories from favorites.
- Added the ability to search for repositories by name.
- Added the ability to add repositories to favorites.
- Added the ability to remove repositories from favorites.

**GitHub Booster section**

- Complete PR title validation system with customizable regex patterns for enforcing PR title conventions.
- Custom validation message support for providing clear feedback when PR titles don't match the expected format.
- Visual feedback with customizable message colors (background, text, and border) for validation messages.
- Option to show validation messages below PR title input when format doesn't match.
- Option to disable PR creation button when title doesn't conform to validation rules.
- Real-time validation with 300ms debounce for optimal user experience.
- Automatic injection of validation components into GitHub's PR creation interface.
- Content script architecture with modular managers for PR validation and GitHub controls.

### Technical Implementation

- Event-driven architecture using custom events for communication between extension popup and content scripts.
- React component injection into GitHub's DOM for seamless integration.
- Regex parsing support for both `/pattern/flags` and plain pattern formats.
- Singleton pattern implementation for consistent state management across components.
- WeakMap-based cleanup for proper memory management of injected React components.

## [1.3.7] - 2025-01-18 🚀

**Release Branch section**

- Renamed 'Refetch' button to 'Generate' for consistency with similar buttons.
- Branch parts no longer move to the end automatically to prevent confusion when enabling/disabling parts.
- Restructured UI to place branch parts sections closer to the resulting branch.
- Repositioned 'Reset Data' button for consistency across pages.

**Config section**

- Improved styling
- Danger zone added to the config section.
- Added download / upload icons.

**Bugs fixed**

- When changing tab after copying command/branch toast now closes properly.

## [1.3.6] - 2025-01-12 🚀

**Global**

- Add the possibility of import/export config (beta).
- Added the ability to reset all states to default in the extension.

### Style fixes

- Improve Branch Convention screen readability.
- Add warning icon to errors.
- Style Task Prefix Sections.
- Style tab underline separately.

## [1.3.5] - 2024-12-29 🚀

### Added

**Workflow**

- Github action automatically updates changelog when there's new changes.

**Config**

- New color theme selector section with 4 new available themes.
  - Dark Moon
  - Frankenstein
  - Night City
  - Half Life

### Fixed

- Tooltip confusing messages removed.
- Add consistency to links hover colors.
- Random word refetch button keeps inherit width when loading on refetching
- Refactor tertiary buttons to improve consistency.
- Automatic scraping won't be triggered if there's no need.

### Technical Debt

- Playwright screen POC removed from code.
- Colors stored in theme variables using SASS.
- Remove toast temporarily until decide best approach.

## [1.3.2] - 2024-12-18 🚀

### Added

**Task Branch section**

- Task prefix checkbox removed
- Task prefix includes sections for Team role, Layers, and Environments to enhance UI/UX.
- Improve UI adding a separator, changing colors and updating position of reset data.

**Release Branch section**

- Drag & Drop approach to release branch creation.
- Branch conventions dialog now includes information about Git branching conventions.

**Config**

- Shortcut to changelog added.

### Fixed

- Tooltips added to improve UI/UX experience.
- Errors added in edge cases.

## [1.3.1] - 2024-11-28 🚀

- Update Theme / marketing.
- Fix trailing dash errors.

## [1.3.0] - 2024-11-22 🚀

### Added

- `Git Branch` command added to creation commands.
- `FE, BE, QA...` added to layer/extra info.
- Integration with Asana.
- Settings Section.
- Automatic Scraping on load with Jira / Asana (Configurable in settings).

### Fixed

- Branch can be formed without task name if wanted.
- Jira buttons are replaced with Asana buttons in the title when using Asana.


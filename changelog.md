# Git Branch Generator: Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.5.0] - Working on PostMessage Debugger 👷🏻‍♂️

### Added

**PostMessage Debugger section**

- Enhanced PostMessage events list with improved visual styling matching QuickCopyTab design.
- Applied consistent border, border-radius, and hover effects to PostMessage items.
- Added proper icon filtering using `var(--icon-main-color-filter)` for all action buttons.
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

**QuickStore section**

- Added the ability to add items to the quick store.
- Added the ability to remove items from the quick store.
- Added the ability to search for items in the quick store.
- Added the ability to add items to the quick store.
- Added the ability to remove items from the quick store.

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


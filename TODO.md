# TODO

## 🔧 Logging & Debugging

- [ ] Integrate `@chrismessina/raycast-logger` for verbose logging
  - [ ] Add `verboseLogging` preference to `package.json`
  - [ ] Create `src/logger.ts` to initialize and export logger instance
  - [ ] Replace all `console.log` calls with `logger.log()` (in `utils.ts`, `brew.ts`)
  - [ ] Replace all `console.error` calls with `logger.error()`
  - [ ] Create child loggers for different modules (e.g., `[Brew]`, `[Cache]`, `[Actions]`)
  - [ ] Add logging for key operations: fetch, install, uninstall, upgrade, cleanup
- [ ] Improve error handling with better user feedback
  - [ ] Add more descriptive error messages in `showFailureToast`
  - [ ] Add error context (command, parameters) to error logs
  - [ ] Consider adding retry logic for transient network errors in `fetchRemote`

## 🗂️ Caching & Performance

- [ ] Implement proper caching for brew data
  - [ ] Add cache TTL configuration option
  - [ ] Add manual cache invalidation action
  - [ ] Consider using SQLite for faster queries (noted in `utils.ts` comments)
  - [ ] Add cache size monitoring/cleanup
- [ ] Optimize search performance
  - [ ] Pre-compute lowercase names for faster filtering
  - [ ] Consider indexing for large formula/cask lists

## 🏗️ Code Organization

- [ ] Restructure codebase for better organization
  - [ ] Move types from `brew.ts` to dedicated `types.ts` file
  - [ ] Split `brew.ts` into smaller modules:
    - [ ] `brew/commands.ts` - brew command execution
    - [ ] `brew/fetch.ts` - data fetching logic
    - [ ] `brew/search.ts` - search functionality
    - [ ] `brew/actions.ts` - install/uninstall/upgrade actions
    - [ ] `brew/utils.ts` - utility functions (brewName, brewIdentifier, etc.)
  - [ ] Move global prototype extensions from `utils.ts` to separate file
  - [ ] Consider extracting toast utilities to `components/toasts.ts`

## 🎨 UI/UX Improvements

- [ ] Add more detailed cask information panels
  - [ ] Show download size
  - [ ] Show installation date
  - [ ] Show SHA256 checksum
  - [ ] Add screenshots/app icons where available
- [ ] Improve icons for outdated packages
  - [ ] Use distinct icons for outdated vs up-to-date (currently both use `CheckCircle`)
  - [ ] Add visual indicator for pinned packages in list view
  - [ ] Consider using `Icon.ArrowUp` or `Icon.ExclamationMark` for outdated items
- [ ] Implement search filtering by category/type
  - [ ] Add filter for taps
  - [ ] Add filter by license type
  - [ ] Add filter for keg-only formulae
- [ ] Add filter for New and Updated packages
  - [ ] Track package update dates
  - [ ] Add "Recently Added" section
  - [ ] Add "Recently Updated" section
- [ ] Add download progress HUD to show download % complete

## 🐛 Bug Fixes

- [ ] Fix issue with the `--[no-]quarantine` switch being deprecated in newer macOS versions
  - [ ] Check macOS version before applying quarantine flag
  - [ ] Update `brewQuarantineOption()` in `brew.ts` to handle deprecation
  - [ ] Consider removing the preference if no longer applicable
- [ ] Fix typo: `pinned_vesion` should be `pinned_version` in `OutdatedFormula` interface

## 📚 Documentation

- [ ] Improve README documentation
  - [ ] Add screenshots of all commands
  - [ ] Document all preferences
  - [ ] Add troubleshooting section
  - [ ] Add contribution guidelines
  - [ ] Document keyboard shortcuts

## 🔮 Future Enhancements

- [ ] Add "brew doctor" command integration
  - [ ] Show health check results in a dedicated view
  - [ ] Add quick-fix actions for common issues
- [ ] Add tap management
  - [ ] List installed taps
  - [ ] Add/remove taps
- [ ] Add formula/cask analytics
  - [ ] Show install counts from Homebrew analytics
  - [ ] Show popularity ranking
- [ ] Add batch operations
  - [ ] Select multiple packages for install/uninstall
  - [ ] Bulk upgrade selected packages
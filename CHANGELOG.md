# Changelog

All notable changes to the `data_prelim` project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [#.#.#] - Unreleased

### Added
-

### Changed
- 
---
## [0.3.0] - 2026-07-07
-  
### Added
- details analysis precip QA/QC specific date within sample range
- given option to run by Continuous Sample Set or Specific Sample ID List
### Fixed
- update the ranking in all excel tab for better visual


---
## [0.2.2] - 2026-04-30
-  
### Added
### Fixed
- update log-file name for better history control, and prevent some warning messge while running scrip in terminal
- update the ranking in all excel tab for better visual
- update the limit of log file, keep in single file
---
## [0.2.1] - 2026-04-30
-  
### Added
-
### Fixed
- update condition to display correct color in user report(DFDK, ENDREC, STARTEND)
- update the review excel file 
- update the condition in tab good sample, bad precent



---
## [0.2.0] - 2026-04-27
-  
### Added
- add new module to dispaly auto correction_pcp using the SOP 304 - NADP (noise detection, false precip, dry Exp code U, full open status code B)
### Fixed
- update condition to display correct color in user report(DFDK, ENDREC, STARTEND)
- update the review excel file 



---
## [0.1.3] - 2026-03-20
-  update condition to display correct color in user report for all sheet excel
### Added
- auto freeze top row, and auto_fit
### Fixed
- update condition to display correct color in user report(DFDK, ENDREC, STARTEND)
### Added
- 



---
## [0.1.2] - 2026-03-18
### Fixed
- update condition to display correct color in user report(DFDK, ENDREC, STARTEND)
### Added



---
## [0.1.1] - 2026-03-18
### Fixed
- Change the digit display in ppt report
### Added
- Added `conditional_format` for user.




---
## [0.1.0] - 2026-03-11

### Added
- Initial release of the Laboratory data review pipeline.
- Support for Excel engines (`openpyxl`, `xlsxwriter`).
- Database connectivity via `pyodbc` and `SQLAlchemy`.
- Configuration management using `.env` files.
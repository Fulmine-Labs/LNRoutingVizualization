# Changelog

All notable changes to this project will be documented in this file.

******************************************

## [1.0.1] - 11/30/2023

### Fixed
hardcoded localhost value in create_grpc_channel #10


******************************************

## [1.0.0] - 11/30/2023
### Added
- Initial release of the project.
- This version includes support for LND and Eclair RTL CSV files as well as gRPC interface to an LND node
- Bugs fixed: 1, 6, 7, 8, 9

### Changed
N/A

### Deprecated
N/A

### Removed
N/A

### Fixed
Output the same graph without using RTL (using data from the Lightning node) ? #1
duplicated check on df existence #6
need better error handling for gRPC request failures #7
some code is running inside a loop the doesn't need to be - performance issue #8
add support for eclair RTL file format #9

### Security
N/A
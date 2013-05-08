# App::SharedLibraryDeps #

Repo: https://github.com/spicyjack/App-SharedLibraryDeps

Shared library dependency tool
- Gets a list of library dependencies for a given library file
- (Optional) gets the name of the package the linked-to library came from
  (if any)
- (Optional) Can use a kernel filelist instead of the system for verifying
  that required files are present in order to satisfy library dependencies

## Todos ##
- Graph dependencies with GraphViz
- App::SharedLibraryDeps::Cache
  - make sure to resolve symlinks somewhere, and store them in the
    file object
  - store symlinks int the cache object, with a reference to the
    original LibraryFile object
- App::SharedLibraryDeps::File
  - Capture package information if requested (`--query-package-manager`)
  - Make this into a role 
    - Basic file attributes
    - Package information
    - Dependency lists
      - Make this into an object, so that multiple lists can be created and
        they all use the same interface
  - Create two new objects to consume it
    - LibraryFile
      - Has forward and reverse dependencies
      - Knows about `linux-[gate|vdso]` and statically linked files
    - BinaryFile
      - Has forward dependencies only

vim: filetype=markdown shiftwidth=2 tabstop=2

# App::SharedLibraryDeps #

Repo: https://github.com/spicyjack/App-SharedLibraryDeps

Shared library dependency tool
- Gets a list of library dependencies for a given library file
- (Optional) gets the name of the package the linked-to library came from
  (if any)
- (Optional) Uses a kernel filelist as input, and walks the filelist to verify
  that all of the library dependencies are present
  - This would need to be done on the donor system to make sure that all
    library files are available for parsing/recursion/verification
- (Optional) Works on other operating systems besides Linux

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

## Dependency Recursion pseudocode ##
- Get a list of dependencies for a file
- For each dependency
  - Is it stored in the cache?
    - Yes 
      - Return cached file object
    - No
      - Turn the file into a file object
      - Run `ldd` to get it's dependencies
      - Classify dependencies
        - Files that are also dynamically linked and not cached, recurse with
          them
          - Return with a list of dependencies; at some point, you should be
            returning with only the ld-linux and linux-vdso files
        - Files that are statically linked or virtual files, add them to the
          cache, then move to the next file
      - Add dependencies to the file object
      - Add reverse dependencies
vim: filetype=markdown shiftwidth=2 tabstop=2

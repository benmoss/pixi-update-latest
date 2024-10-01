# pixi update --latest

Example showing the problem when you cannot update a dependency.

```
$ pixi update python
✔ Lock-file was already up-to-date
```

This is the ideal error that would be surfaced to the user to demonstrate why it is not possible to update to the "latest" version of Python:

```
$ pixi add python==3.12.6
  ⠙ default:osx-64       [00:00:00] loading repodata
  ⠙ default:linux-64     [00:00:00] loading repodata                                                                                                          × failed to solve the conda requirements of 'default' 'osx-arm64'
  ╰─▶ Cannot solve the request because of: The following packages are incompatible
      ├─ libffi ==3.3 can be installed with any of the following options:
      │  └─ libffi 3.3
      └─ python ==3.12.6 cannot be installed because there are no viable options:
         └─ python 3.12.6 | 3.12.6 | 3.12.6 would require
            └─ libffi >=3.4,<4.0a0, which cannot be installed because there are no viable options:
               └─ libffi 3.4.2 | 3.4.2 | 3.4.2 | 3.4.2 | 3.4.2 | 3.4.2, which conflicts with the versions reported above.
```

AntiDrive
=========

Reversing Google Drive and other goodies ;)

Reversing Google Drive
======================

1. Download Google Drive and install it (or use 7-Zip to extract the
   resources from the .msi file).

2. ``googledrivesync.exe`` file is "fat" and looks interesting, right?

3. Download a special version of PyInstaller.

   ::

      $ git clone https://github.com/kholia/pyinstaller.git -b AntiDrive

      $ cd pyinstaller

4. Extract stuff from ``googledrivesync.exe`` file.

   ::

      $ python utils/ArchiveExtractor.py googledrivesync.exe
      [+] magic found at 6125
      Extracting bytecode to output/osx.pyc
      ...
      Extracting bytecode to output/common/worker.pyc
      Extracting bytecode to output/wx/html2.pyc
      Extracting bytecode to output/encodings/punycode.pyc
      Extracting bytecode to output/common/cloud_snapshot_diff_helper.pyc
      Extracting bytecode to output/windows/cacheinvalidation.pyc
      Extracting bytecode to output/encodings/cp1258.pyc
      Extracting bytecode to output/common/snapshot_sqlite.pyc
      Extracting bytecode to output/win32com/client/CLSIDToClass.pyc
      Extracting bytecode to output/encodings/latin_1.pyc
      Extracting bytecode to output/tokenize.pyc
      ...
      Extracting source to output/_mountzlib.py
      Extracting source to output/useUnicode.py
      Extracting source to output/versioneddll.py
      Extracting source to output/win32comgenpy.py
      Extracting source to output/main.py

5. De-compile the bytecode files using uncompyle2.

   ::

      $ uncompyle2 output/common/worker.pyc
      pass

   ;)

5. Study the soure-code, find bugs and make Google Drive better!


Credits
=======

* uncompyle2

  - https://github.com/wibiti/uncompyle2

  - https://github.com/Mysterie/uncompyle2

* PyInstaller

  - https://github.com/kholia/pyinstaller/tree/AntiDrive

  - https://github.com/pyinstaller/pyinstaller

TOD0
====

* dump bytecode from memory (revive pyREtic).

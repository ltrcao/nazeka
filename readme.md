This is a fork of [Nazeka](https://github.com/wareya/nazeka).

# Settings

See the [tutorial](https://github.com/ltrcao/nazeka/blob/master/tutorial.md#settings).

# Building

Build process requires python and lxml, or an existing copy of the extension to rip JMdict#.json from.

- Download JMdict.gz from http://www.edrdg.org/jmdict/edict_doc.html
```bash
curl http://ftp.monash.edu/pub/nihongo/JMdict.gz | gunzip > etc/JMdict
```
- Convert it to json with etc/process.py
    -  Ensure python and lxml are installed, e.g. depending on your Linux distro, something like
```bash
sudo apt update
sudo apt install python3 python3-pip
pip install --user --upgrade pip
pip install --user lxml
```
    - Invoke process.py, after JMdict has been extracted into etc/
```bash
cd etc
./process.py
```
- Move the output to under dict/ so that [...]/dict/JMdict1.json and others exist in that location relative to [...]/manifest.json
    - Basically, after the above commands:
```bash
mv JMdict*.json ../dict
```
- Make sure every .json file is listed as available to the extension in manifest.json - if jmdict added a lot of words, there might be more than 11 files now
- Package as an extension for your browser of choice, or load it as a temporary/indev extension using your browser's development tools

# Copyright and License

Copyright 2017~2019; Licensed under the Apache License, Version 2.0: https://www.apache.org/licenses/LICENSE-2.0

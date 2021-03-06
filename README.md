# wiktionary-derivations-parser

For foreign editions of Wiktionary, extract derivations on each page (if they exist).

## Input

A `.zim` file that contains all pages of a given edition of Wiktionary.

- Wiktionary dumps in `.zim` format can be obtained from [kiwix](https://download.kiwix.org/zim/wiktionary/).

For now, we are dealing with individual `.html` pages from the editions we're working on. For example [gène in French edition](https://fr.wiktionary.org/wiki/g%C3%A8ne).

## Output

Each derivation tuple consists of these fields (UNFINISHED):

- `edition`: the edition of Wiktionary the derivation is from. It is a 2-3 letter code used in the Wiktionary url.
- `headword`: the word that is being derived.
- `lang`: the language of the `headword`. It might be different from the language of the edition.
- `derivation`: the derivation of the `headword`.
- `pos`: the part of speech of the `headword` in `lang`.

The output is a `.csv` with these columns.

## Dependencies

- `beautifulsoup4`: used for parsing html.
- `requests`: used to make http calls and fetch `.html` from the Intenet. Will eventually be removed as we will be dealing with locally stored files.
- `pycountry` and `iso-639`: used for conversion between language codes.

Install in a `virtualenv` as appropriate.
To install all dependencies:

    $ pip install -r requirements.txt

To install one by one, use `pip install [PACKAGE NAME]`. 

## Usage
 
To run with a `.zim` file:

    $ python parser.py -z [zimfile]

- Support for using `.zim` file has only been tested for `Python 3.5`. It is probably not working for `Python 2` at this moment.

Detailed usage:

    usage: parser.py [-h] [--zim ZIM] [--edition EDITION]
    optional arguments:
      -h, --help            show this help message and exit
      --zim ZIM, -z ZIM     use zim file instead of html
      --edition EDITION, -e EDITION
                            explicitly specify the language edition



## Common

The list of common things in different editions are listed in [common.md](common.md).

## Todo

- Write parsers for two or three editions using the translation parsers.
	- Run parsers on zim files (entire foreign editions of Wiktionary)
- Generalize them and create a skeleton for writing other parsers.
  - make it so that we need minimal changes in order to parse another edition
- Generate parsers for editions of interest.

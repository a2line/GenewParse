# NAME

genea.pl - GenewParse

# VERSION

version 1.5

# SYNOPSYS

Parseur de tableau généalogique geneweb vers un fichier CSV, prêt pour le réimport.

## License : GPL

## Changelog

- 0.8 : 28/05/18 : Early debug
- 0.9 : 28/05/18 : First CSV output
- 1.0 : 29/05/18 : Formalisation, constants, dates bugfix, first versioned release
- 1.1 : 29/05/18 : Multiple verboses, date precision handling improvement
- 1.2 : 29/05/18 : Return back to initial CSV format, revolutionnary calendar dates handling, add precision on année, uppercase ; diacritics handling.
- 1.3 : 30/05/18 : Change Switch module to given - switch limit - help page - debug dates & accents, Fix logical bug de logique for caps - unicode normalization on split/combined mode
- 1.4 : 30/05/18 : Tree display
- 1.5 : 31/05/18 : input/output files + curl handling

## Dependencies :

### CPAN 

- ```Text::Unidecode qw(unidecode);```
- ```HTML::Entities qw(decode_entities);```
- ```Unicode::Normalize;```

Install them with "cpan -i Text::Unidecode qw(unidecode) HTML::Entities qw(decode_entities) Unicode::Normalize"

# DESCRIPTION

Il parse le résultat d'un curl sur l'URL de votre geneweb, via STDIN

Il effectue le nettoyage des dates, normalisation Unicode, mise en forme des patronymes sous forme cononique.
La transformation des dates républicaines, et du nettoyage cosmétique.

# USAGE

```
genea.pl [-v <LEVEL>] [-l <SOSA>] [-t <LEVEL>] [-i <INPUT> [-u <URL>] ] [-o <OUTPUT>] [-h|-?]
        -v <LEVEL>  : with <LEVEL> value between 0 (quiet) et 6 (Xtra Trace)
        -l <SOSA>   : only process sosa <SOSA>
        -t <LEVEL>  : Tree format display, by patronym branch, with <LEVEL> as maxdepth
        -i <INPUT>  : input file. If this flag is omitted, the parser will use STDIN
        -u <URL>    : URL to fetch and save to INPUT file, before processing this file. -i is mandatory, the file will be replaced.
        -o <OUTPUT> : Output file. If omitted, will use STDOUT.

Be careful. The order of the switches is important, and CURL on <URL> is done immediately, before looking up at the other switches.

```


Verbose levels:
- XTRACE  => 6,
- TRACE   => 5,
- DEBUG   => 4,
- INFO    => 3,
- WARN    => 2,
- ERR     => 1,
- CRIT    => 0


# Nationalities

> Dataset of 100 common nationalities

## Data

### `nationalities-common`

[![](https://img.shields.io/badge/nationalities-145-brightgreen.svg?style=flat-square)](nationalities-common.txt)

Handpicked dataset of nationalities you will know (western perspective).

See: [`txt`](nationalities-common.txt), [`json`](nationalities-common.json)

### `nationalities-unfiltered`

[![](https://img.shields.io/badge/nationalities-217-brightgreen.svg?style=flat-square)](nationalities-unfiltered.txt)

Unfiltered list of nationalities that includes:

- country names that double as nationalities (like Luxemburg)

See: [`txt`](nationalities-unfiltered.txt), [`json`](nationalities-unfiltered.json)

## Source

The orignal data source is: [faru-khan/countries_nationalities_en_ar](https://github.com/faru-khan/countries_nationalities_en_ar)

## See also

More datasets:

- [animal names](https://github.com/jneidel/animal-names)
- [job titles](https://github.com/jneidel/job-titles)

## Transforms

These are the transfomations I applied to the data (along with some manual picking out.)

To get `nationalities-unfiltered.txt` from the source file:

```sh
<SOURCE jq ".[].nationality_en" $INPUT | cut -d\" -f2 | grep -ve " or " -e " and "
```

From `txt` to `json`:

```sh
<FILE.txt awk -F@ 'BEGIN { print "[" } { print "  \""$1"\"," }' | sed '$ s/,$/\n]/'
```

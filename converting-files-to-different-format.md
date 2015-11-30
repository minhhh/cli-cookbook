# Converting files to different format

## Problem
You want to convert a file to/from different formats

## Solution
`iconv` can be used to easily convert files from one character set to another

```
    # convert from UTF-8 to ISO-8859-15/latin-1
    iconv -f UTF-8 -t ISO-8859-15 <infile> > <outfile>
```

`recode` can do the same thing but `in-place`
```
    recode UTF8..ISO-8859-15 <infile>
```

`recode` can also be used to convert line endings
```
    # convert newlines from LF to CR-LF
    recode ../CR-LF <infile>

    # base64 encode file
    recode ../Base64 <infile>
```

`recode` can also combine transform character set, line endings and encode

```
    recode utf8/Base64..l1/CR-LF/Base64 <infile>
```

# YAML Basics
Yet another markup language...

It is a data serialization language for a configuration file that is easy to read. Based on popular agile languages for structure (arrays, sequences, matching etc.) And easy to human configure.

### Syntax

Spaces not tabs

Indent for structure (grouping together)

Dashes for lists

`:` denote a key value pair.

~~~yaml
host: phl-42
datacenter:
  location: Philidelphia
  cab: 13
roles:
   - web
   - dns
~~~

### Writing YAML
#### Block Style
Better for humans, less compact, most familiar to see
#### Flow Style
extension of JSON, folding long lines of content, tags and anchors

### Mappings
Associated Arrays, hash tables, key value pairs, collection. They are denoted with `:`. Cannot have duplicates on same level/indent. Or use bracket {} for flow style.
~~~yaml
host: phl-42
datacenter:
  location: Philidelphia
  cab: 13
~~~

### Sequences, Lists and Arrays
Denoted with `-`. Or square brackets in flow style.

~~~yaml
roles:
 - webserver
 - wp_database
datacenter:
  - location: Philidelphia
  - cab: 13
  - ""
~~~

### Scalars
String, number, or boolean. Use "" or '' to make number to strings and \n for new line. location and philidelphia are both scalars mapped to eachother. Value with mutiple lines is `|`. Folded style (convers line to single space) will show up as one long line. Can add space to preserve lines with second indent.

~~~yaml
datacenter:
  - location: Philidelphia
  - cab: "13"
  - ""
downtime_sch: |
  2018-10-31 - kernbal upgrade
  2018-02-02 - security fix
comments: >
 Experiencing high I/O
 since 2018-10-01
 Currently investigating
~~~

### Structure

"---" denotes start of file. So you can do multiple documents in one file. "..." to mark end without closing data stream

~~~yaml
---
host: phl-42
datacenter:
  location: Philidelphia
  cab: 13
roles:
   - web
   - dns
---
host: phl-43
datacenter:
  location: Philidelphia
  cab: 14
roles:
   - web
   - dns
...
---
host: hel-13
datacenter:
 location: Helsinki
 cab: "9"
 cab_unit: "5"
~~~

### Comments
Defined with octothorpe and white space (# ). Can be placed on own line. Inline comments okay too. Cannot  be placed in scalars. Not read by computer, for humans. Blank lines are read as comments. NEED the SPACE.

~~~yaml
---
# hello 
host: phl-42 # hi
datacenter:
  location: Philidelphia
  cab: 13
roles:
   - web
   - dns
---
~~~

### Tags
Used for setting URI, can set local tags, and a data type.


Set a URI - Use the `%TAG !` prefix. `tag` is the prefix here.
~~~yaml
%TAG ! tag:hostsdata:phl
~~~

Set a local tag. Single exclamation, no space

~~~yaml
datacenter:
    location: !PHL Philidelphia
~~~

Set data types with two exclamation points (!!). Forces data type.
~~~yaml
cabinet !!str 13
cabinet !!str 2
~~~

### Anchors
Store and reuse data within yaml file. Certain lines get reused throughout, use as sub for copy and paste.

Define anchor with `&` and reference with a `*`

Anchor a single scaler.

~~~yaml
--- 
host: phl-42
datacenter:
  location: &PHL Philidelphia
  cab: 13
roles:
   - web
   - dns
  location: *PHL
---
~~~

Can do collections too
~~~yaml
roles: &wphost
 - webserer
 - wp_dataset
...
---
roles: *wphost
~~~
---
title: Advanced Searching
id: advancedsearching
milestone: help.advancedsearching
---

# Advanced Searching $10$

This section documents the special term types and operators that are available in $ProductShort$.

- Single Terms
  - Plain Text Words
  - Exact Phrases
- Multiple Terms
  - Match all the words
  - Match any of the words
  - Exclude some words
- Operators
  - Logical Operators: `AND`, `OR`, `NOT`
  - Sequence Operators: `BEFORE`, `AFTER`
  - Proximity Operators: `IN`, `INTERSECTS`, `EQUALS`, `BEFORE` _`n`_, `AFTER` _`n`_, `WITHIN` _`n`_, `NEAR`
  - Wildcards
- Grouping
- Additional Search Types and Modifiers
  - Data Type References
    - Bible References
    - Morph References
    - Bible Senses
    - Factbook References
    - Other Data Types
  - Term Modifiers
    - Language
    - Search Fields
    - Mark Sensitivity
  - Extension Terms
    - Milestone
    - Section
    - Highlight
    - Speaker/Addressee
    - PassageList
	- Headword
    - Label

Note that some kinds of searches can only be run against datasets that are available in different packages, so some of these searches may not produce results, depending on the library.


## Single Terms

Most queries will be for a single term, such as `love`.


### Plain Text Words

Typing `love` will match any instance of the word "love."

Select from the Search options to change how typed words are matched against resource text.

If `~Match case` ![](../../Images/case.png) is selected, then typing `God` will not match "god" with a lowercase "g."

If `~Match all forms` ![](../../Images/form.png) is selected, then all forms of the word will be found. As a result, typing `love` will match _love, loves, loved, loving, lover, lovers_.

> Note: This is an algorithmic process, and while it is mostly quite accurate, it will sometimes match similar words that are unrelated to the query, or may result in archaic or obscure forms of a word not being matched.

Language modifiers can be used to specify the language for a word, though they are not strictly necessary. So, entering `g:` and then a [transliteration](../Glossary/transliteration.md) of a word, for example type `g:logos`, allows users to select `~λόγος` from the drop-down suggestion list. The transliterated input has now transformed using the language's native alphabet. To type Hebrew or Aramaic, start with `h:` and `a:` respectively. However, entering `logos` in the search box also allows the same option.

For more details about typing Greek and Hebrew/Aramaic using transliteration, see [untransliteration](../Glossary/untransliteration.md).


### Exact Phrases

Put exact phrases in simple quotes: `"son of man"` rather than `son of man`. The first query searches for a single term consisting of the entire phrase. The second, without quotation marks, is a search for each word separately. Without quotes, the three words can appear in any order and at any distance apart so long as they are in the same article or verse.


## Multiple Terms

When a query consists of multiple terms, each term is given a different color in the search results. It is possible to construct the query to match all, some, or any of the terms.


### Match all the words

By default, all of the terms in the query must be present for the result to be returned. To find articles (in Bible Search, verses or chapters) that have all the words _faith_ and _hope_ and _love_, type `faith hope love`. This is equivalent to `faith AND hope AND love` (see more about the `AND` operator below).

By default, terms are allowed to match in any order and at any distance from one another within the unit being searched (articles in Books Search, verses or chapters in Bible and Morph Search). To force one term to be before or after another, or to be a particular distance away, some extra operators will be necessary.


### Match any of the words

To match any of the words _faith_ or _hope_ or _love_ in any order, use `faith OR hope OR love`. `OR` must be entered in uppercase to $ProductShort$ from searching for the word "or" in addition to the entered terms.

To group mutiple terms together so they are only counted once and receive the same color highlight, search using the `term` keyword. For example:

- `term:(faith OR hope OR love)` returns every verse (or passage) containing any of those words, but any verse (or passage) containing more than one of the terms is only counted once and every instance of faith, hope, or love receives the same highlight color.


### Exclude some words

Some may want to exclude a term from search results. For example, one may want to find all the verses with "works," but not if they also contain the word "faith." To do this, enter `faith NOT works`. Again, `NOT` must be entered in uppercase.


## Operators

Operators express relationships between terms. So, `faith AND works` tells the search engine that both `faith` and `works` must be present for a result to match, where `faith OR works` means that either term may be present, and `faith NOT works` means that `faith` only must be present, and not `works` or the verse is not a match.

> Note that operators must be typed in ALL CAPS, so `heavens AND earth` is a search with two terms, where `AND` is an operator between them, and `heavens and earth` is three terms with no operator, but the text of the word "and." This distinction helps the search engine know what is meant when typing `AND` versus `and`, `OR` versus `or`.

To search for a word that is spelled the same as an operator, enter it in anything other than all caps (so `and` or `And`). In the rare event that you want to search for an all caps version of a search operator in text (such as searching this help resource!), enclose the all caps word in quotes (`"AND"`).


### Logical ("Boolean") operators

The basic logical operators are:

`AND` -- `this AND that` -- Both terms must be present.

`OR` -- `this OR that` -- Either term must be present (or both is okay, too).

`NOT` -- `this NOT that` -- The left term must be present and the right side must not.


### Sequence Operators

Sequence operators specify the order the query terms must appear in:

`BEFORE` -- `this BEFORE that` -- The left term must appear before the right term in the result.

`AFTER` -- `that AFTER this` -- The left term must appear after the right term in the result.


### Proximity Operators

Proximity operators force the terms to be a certain distance apart within the result.  or perhaps to overlap with each other.

Many texts, especially Bibles, have tagging which overlaps with other tagging, or with the resource text. For example, a Bible might have a Greek lemma or Strong's number that overlaps with the surface text of the Bible. Or, it might have tagging indicating who the speaker is that overlaps with the words they spoke. Several proximity operators are designed to help find overlapping tagging. Generally, it is best to use INTERSECTS, unless one is sure an alternative is needed:

- `INTERSECTS` -- `speaker:Jesus INTERSECTS faith` -- Will find everywhere where text with Jesus marked as the speaker intersects in any way with the word faith (i.e., everywhere Jesus spoke a word translated as "faith").

- `EQUALS` – `lemma.g:λόγος EQUALS message` – Will find everywhere where the Greek lemma λόγος is in exactly the same location as the word message (i.e., everywhere λόγος is exactly translated as "message").

- `IN` – `repent IN literaryTyping:Evangelistic` – Similar to INTERSECTS, but the first term has to be wholly contained in the second term. Unlike INTERSECTS, the first term can’t start before the second term, nor end after it. 

Other proximity operators help find where terms are a certain distance apart. The _distance_ between two terms is specified with a number and a unit. Available units are:

- `CHAR` or `CHARS` -- Counts characters from the end of the left term to the first character of the right term. So, two words separated by a single space are `2 CHARS` away from one another.

- `WORD` or `WORDS` -- Counts words from the end of the left term to the position of the right term. So, two adjacent words are `1 WORD` apart, and "son" and "man" in "son of man" are `2 WORDS` apart.

The number of `CHARS` or `WORDS` can be specified as either a number (`2 CHARS`) or as a range (`1–10 WORDS`). The count is inclusive of the right term, so a distance of `1 CHAR` means the right term begins the very next character after the left term ends, that is, with zero intervening characters. (This is useful for searching for Hebrew morph segments, such as inseparable/prefixed prepositions.) A distance of `1–10 WORDS` means the right term is as few as one or as many as ten words away. (i.e., There can be as few as zero or as many as nine words in between the left and right term.)

The proximity operators are:

- `BEFORE _distance_` -- `son BEFORE 2 WORDS man` -- Will match "son" before "man" with one word in between.

- `AFTER _distance_` -- `man AFTER 2 WORDS son` -- Will match "man" after "son" with one word in between.

- `WITHIN _distance_` -- `suffering WITHIN 1-10 WORDS glory` -- Will match "suffering" and "glory" in any order with zero to nine words in between.

- `NEAR` -- `suffering NEAR glory` -- Equivalent to `WITHIN 1–48 CHARS` (within 8-10 words on average).

- `THEN` -- `Jesus THEN Christ` -- Equivalent to BEFORE 1-1 WORDS, but the overall expression is treated as a single term.


### NOT Operators

A NOT operator subtracts matches on the right side from what is on the left. For example, `Jesus NOT Christ` will return verses that include the word "Jesus," but don’t include the word "Christ."

`NOT` can be combined with any of the proximity operators above. For example, `lemma.g:λόγος NOT EQUALS message` will return everywhere λόγος is translated as something other than "message."


### Grouping

It will sometimes be necessary to resolve some ambiguities when using multiple terms and search operators.

When typing `this OR that AND another`, the intention may be `(this OR that) AND another` or it may mean `this OR (that AND another)`. Adding the parenthesis removes the ambiguity.


### Wildcards

Wildcard symbols can be used to represent zero or more characters in a word.

-	`*` represents any number of characters in a word.
-	`?` represents a single character in a word (or zero characters at the end of a word).

For example:

-	`Christ*` -- finds "Christ", "Christian", "Christlike", etc.
-	`lord?` -- finds "lord" and "lords", but not "lorded" or "lord’s".
-	`s?n` -- finds "sin", "son",and "sun", but not "soon".

> A wildcard will not match punctuation, spaces, or anything else that separates words. So, `Jesus?Christ` and `Jesus*Christ` will not return “Jesus Christ”.


## Keywords

In addition to plain text searches (such as `Judah`), $ProductShort$ also allows users to search a specific [data type](../Glossary/datatype.md), such as `person:"Judah (patriarch)"` or `place:"Judah (kingdom)"`.

The type of term determines which dataset or kind of data will be matched. Searching for the _text_ `Judah` will only match those characters in sequence, whereas searching for the reference `person:"Judah (patriarch)"` (depending on the library and datasets) will not match where "Judah" refers to the place or the tribe, but will match places where the text "he" or "his" has been tagged as referring to the biblical person Judah, son of Jacob.

It is recommended to type in the search term, and then to pick the desired information attached to the word from the drop-down term picker that appears.

> Enter `judah` and the text term `Judah`, the person term `person:"Judah (patriarch)"`, and many other matching terms will be returned.

Right-clicking a word in a resource is a fast way to get just the right term to search on.


### Data Type References

A [data type](../Glossary/datatype.md) is a kind of data, or the pattern for a reference scheme. The Bible follows a book, chapter, verse scheme with a certain set of books, with a certain number of chapters in each book, and a certain number of verses in each chapter.

To search for a [data type reference](../Glossary/datatypereference.md), enter the name of the data type (for example `bible`), then a colon (:) and an optional data type matching operator (more below), then a string that specifies what reference you want to match (for example `Jn 3:16`). The example `bible:"Jn 3:16"` will match John 3:16 no matter how it is "spelled" in the resource: "Joh. iii, 16".

Some data types allow for references to be matched with varying levels of exactness. This is specified by optional data type matching operators: `=`, `<<`, `>>`, or `~~`. Each data type uses these operators differently, but in general:

- 	`=` matches the exact value.
-	`<<` matches any reference wholly included in the search value (ie. Jn 3:16 and Jn 3:16b).
-	`>>` matches any reference that includes the whole search value (ie. Jn 3:16 as found within Jn 3:1-21).
- 	`~~` matches the specified reference loosely or generously (includes all results found in `<<` and `>>`).
- 	If no optional datatype matching operator is supplied, the software will determine how loose or precise the matching is.

[`~Reference matching`](../Searching/referencematching.md) adjusts the specificity of the search results. 

- Narrow ![](../../Images/Precise.png) is the most precise search that only uses the specified datatype(s).
- Default ![](../../Images/Medium.png) returns results from other datatypes with a similar value, such as `topic:"Jesus Christ"` and `person:Jesus`.
- Broad ![](../../Images/Broad.png) provides results that are equivalent to what was entered. For example, searching for `"Holy Spirit"` would also display results for "God the Spirit" and "Paraclete". 

The most common data type to search for in $ProductShort$ is Bible references, for example, `bible:"John 3:16"`.

When beginning a data type search, users can click the plus button ![](../../Images/plus2.png) on the search bar immediately to the left of the keyboard selector to choose from the many available data types.


#### Morph References

The most basic way to start searching for morph terms is to right-click a word in a morphologically tagged resource or a reverse interlinear Bible and choose the data type from the left side of the [Context menu](../Resources/contextmenu.md). Several options to search for that data type reference will appear on the right side.

Use a [Morph Search](../Searching/morphsearch.md) and type `g:` or `h:` or `a:` to specify a Greek, Hebrew, or Aramaic lemma (or `lemma.g:` to specify a lemma, language, and morph scheme), `root:` to specify a root form, `surface:` to specify the surface text, or `@` to start a morph term. 

For example:

- Lemma -- `lemma.g:λόγος` -- Specifies a lemma (λόγος), within a given language and morphological analysis (`lemma.g`). To learn how to search against other morph schemes, see below.
- Root -- `root.h:חסד:2` -- Specifies a root form.
- Morphology -- `@VaW[^2]MS` or `morph.h:~VaW[^2]MS???` -- Specifies a cluster of morphological properties against a given morph scheme.

> Learn more about [how to type Greek or Hebrew/Aramaic](../How-To/howdoientergreekorhebrewtextandswitchbetweenkeyboards.md).

A "morph scheme" refers to a particular morphological and lexical analysis of a set of texts. Each scheme represents a perspective on how word properties should be documented, or how a lexicon ought to be organized. Most scholars agree that there are nouns and verbs in Hebrew, but not all agree on how to best describe the various kinds of Hebrew verb stems. Nor does every lexicon divide and number homographs in the same way, or spell lemma forms in the same way.

Morph schemes and their corresponding data types include:

*Aramaic*

- Andersen-Forbes Aramaic Morphology -- `morph.af.a:...`
- Comprehensive Aramaic Lexicon Morphology (CAL) -- `morph.cal.a:...`
- Logos Aramaic Inscriptions Morphology -- `morph.ins.a:...`
- Logos Aramaic Morphology -- `morph.a:...`
- Stuttgart Electronic Study Bible (SESB) Aramaic Morphology -- `morph.sesb.a:...`
- Werkgroep Informatica (WIVU) Aramaic Morphology -- `morph.wivu.a:...`
- Westminster Aramaic Morphology -- `morph.west.a:...`

*Greek*

- Friberg Greek Morphology -- `morph.fr.g:...`
- GRAMCORD Greek Morphology -- `morph.gr.g:...`
- Logos Greek Morphology -- `morph.g:...`
- Robinson Greek Morphology -- `morph.rob.g:...`
- Swanson Greek Morphology -- `morph.sw.g:...`

*Hebrew (including Semitic inscriptions)*

- Andersen-Forbes Hebrew Morphology -- `morph.af.h...`
- Logos Hebrew Morphology -- `morph.h:...`
- Logos Semitic Inscriptions Morphology -- `morph.ins.h:...`
- Stuttgart Electronic Study Bible (SESB) Hebrew Morphology -- `morph.sesb.h...`
- Werkgroep Informatica (WIVU) Hebrew Morphology -- `morph.wivu.h:...`
- Westminster Hebrew Morphology -- `morph.west.h:...`

*Latin*

- Logos Latin Morphology -- `morph.l:...`

*Syriac*

- Leiden Peshitta Institute Syriac Morphology -- `morph.lpi.s:...`
- Sedra 3 Syriac Morphology -- `morph.s3.s:...`

*Transliterated*

- Biblia Hebraica Transcripta (BHt) Morphology -- `morph.bht.t:...`


#### Bible Senses

Senses are indivisible units of meaning as defined by the Bible Sense Lexicon dataset. Every noun, verb, adjective, and adverb in the Bible has been assigned a sense.

For example, `sense:"to cure"` finds various places where curing happens. But "to heal" is a type of curing as well.

- `sense:>>"to cure"` -- Finds this sense and all broader senses.
- `sense:~"to cure"` -- Finds this sense and all narrower or broader senses.
- `sense:="to cure"` -- Finds exactly this sense.

The easiest way to specify a Sense term is to type a word into the Search box and choose a Sense term from the drop-down suggestion list, or to right-click a word in a reverse interlinear Bible and choose a Sense from the right side of the [Context menu](../Resources/contextmenu.md).


#### Factbook References

Several data types associated with [Factbook](../Tools/factbook.md) pages can be searched for in resources and in [Factbook Tags](../Resources/factbooktags.md).

These can be searched for directly:

- `~Person` -- `person:Jesus` -- Finds mentions of biblical persons.
- `~Place` -- `place:Jerusalem` -- Finds mentions of biblical places.
- `~Thing` -- `thing:Dog` -- Finds mentions of biblical things.
- `~Topic` -- `topic:Law` -- Finds mentions of topics.
- `~Biography` -- `biography:"John Wesley"` -- Finds mentions of non-biblical notable persons.

> Note that the search strings for all of these data types must exactly match the primary label of the person/place/etc., and that they are case-sensitive. Only `person:"Simon (Cyrene)"` will match Simon of Cyrene. Neither `person:"Simon of Cyrene"` nor `person:"simon cyrene"` will work. It's best to use the term picker in the Search panel or to use the Context Menu to find terms.

The Logos public wiki has a [comprehensive listing of data types](https://wiki.logos.com/List_of_Datatypes) and their abbreviated search aliases.


## Term Modifiers

Search terms can be modified to include extra information such as language, search fields, and sensitivity to diacritical markings.

Term modifiers apply to the term they are attached to, to the group of terms (surrounded by parenthesis) they are enclosed within, or to the entire query.


### Language

To specify the language of a search term, type the name of the language in front of the term with a colon. For example, `french:pain` and `english:pain` are different words.

- `french:pain AND german:brot` -- Finds texts that include both the French word "pain" and the German word "brot."
- `french:(pain AND chair)` -- Finds texts that include the two French words, "pain" and "chair."


### Search Fields

A search field is a portion of text that has been specially tagged so it can be searched exclusively. For example, text found in headings, rather than in the body of the text, is said to be in the `heading` field. Click `~All Text` at the top of the search panel and expand `Search Fields` to see the available fields.

Fields are searchable using the same syntax format described above.

-	`field.bible:people` -- Returns results from the _text_ of the Bible containing the word "people." The text, `field.`, is only needed to prevent ambiguity with keywords like `bible`.
-	`woc:people` -- Matches "people" only in the "Words of Christ" field.
-	`footnote:bible:="Jn 3:16"` -- Finds exact references to John 3:16 in footnote text.

Fields can also be applied to multiple terms at once.

For example: `footnote:(justification AND sanctification AND bible:"Romans 5–7")`

Resources support many different search fields. To find out what search fields a given resource supports:

1. Open the resource.
2. Open the Panel menu ![](../../Images/KebabVertical.png)in the top-right corner of the resource. (Or press `Ctrl`+`Shift`+`I` / `Shift`+`Cmd`+`I`).
3. Click `~Information`.
4. Search fields available in the resource will be listed under the heading `~Search Fields` near the bottom of the resource information.

Choose search fields from the `~All Text` search parameter at the top of the Search panel.


### Mark Sensitivity

Terms can be modified to count diacritic marks as significant or not significant for matching. Defaults vary by language. For example, English generally doesn't have diacritic marks, so by default typing `resume` will match _resume, resumé, and résumé_. To override this default, specify a marks matching term modifier into the query.

- 	`match.marks:` -- Makes all non-spacing marks significant.
- 	`match.nomarks:` -- Ignores all non-spacing marks, regardless of language defaults.
-	`match.form:` -- Ignores stemming.
- 	`match.exact:` or `match.all:` -- Matches exactly what you type.
- 	`match.case:` -- Matches sensitive to capital/lowercase letters.

Some languages have special mark-matching rules.


#### Hebrew/Aramaic

By default, Hebrew is not sensitive to any marks in the query, except for sin and shin dots, which are like the slash in Swedish ø: they are different letters. (This can be overridden with `match.nomarks`.) Additionally, maqqef and space are treated as equivalent.

- 	`match.vowels` -- Vowel diacritics in the query will be treated as significant for matching.
- 	`match.dagesh` -- Dagesh in the query is significant.
- 	`match.accents` -- Cantillation diacritics (_te'amim_) will be treated as significant.
- 	`match.massora` -- Matches the masora circle.
- 	`match.rafe` -- Matches accent rafe.
- 	`match.critical` -- Matches text-critical marks.
- 	`match.pointed` -- Same as `match.vowels`, `match.dagesh`, `match.massora`, `match.rafe`, and `match.critical`.
- 	`match.cantillated` -- Same as `match.vowels`, `match.dagesh`, `match.massora`, `match.rafe`, `match.critical`, and `match.accents`.
- 	`match.holem-haser` -- Differentiates between holem and holem haser.

#### Greek

By default, Greek searches are not sensitive to any marks in the query.

- 	`match.iota-subscript` -- Subscripted iota is significant.
- 	`match.dieresis` -- Dieresis mark is significant.
- 	`match.breathing` -- Rough and smooth breathing marks are significant.
- 	`match.accents` -- Includes all accenture marks.
- 	`match.technical-marks` -- Includes technical diacritics.
- 	`match.unaccented` -- Doesn't count marks except for rough and smooth breathing.
- 	`match.polytonic`

#### Syriac

By default, Syriac is not sensitive to any marks.

- 	`match.vowels`
- 	`match.silent`
- 	`match.begadkephat`
- 	`match.grammar`
- 	`match.barrekh`
- 	`match.music`
- 	`match.accents`
- 	`match.dialect`
- 	`match.abbrev`


### Extension Terms

$ProductShort$ allows specialized searches of content an tools within the software, for example, `passageList:...` or `highlight:...`. The Highlight extension, for example, will search the names of highlighter styles. The drop-down selector for field or highlighting will not be applied to these search extensions.


#### Milestone

A search for `bible:"Jn 3:16"` will find _citations_ of John 3:16 (or citations that include John 3:16, such as John 3:1-36), but will not find the text _of_ John 3:16 in a Bible or text _about_ John 3:16 in a commentary. To search for this, use the [Milestone](../Glossary/milestones.md) extension term.

For example:

- `milestone:bible:"John 3:16"`
- `milestone:josephus:"Wars of the Jews I, ii 3"`

#### Highlight

The Highlight extension term finds text highlighted with a specific highlighting style. The content specifies the name of a highlighter style, with the palette name as necessary.

- `highlight:"StyleName"` -- Finds highlights using the entered style name.
- `highlight:"PaletteName/StyleName"` -- Use if the style name appears in several palettes.
- `highlight:"PaletteName/*"` -- Finds text marked with any style in that palette.
- `highlight:*` -- Finds all highlights.

For example:

- `highlight:"Darkness"` -- Finds all highlights in the "Darkness" style.
- `highlight:"Bible Study/Darkness"` -- Finds highlights for the "Darkness" style in the "Bible Study" palette.
- `highlight:"Bible Study/*"` -- Finds all highlights in the "Bible Study" palette.

> Avoid creating Styles or Palettes with a slash (/) in their name.

#### Speaker/Addressee

The Speaker and Addressee search extensions search the _Reported Speech_ and _Addressees in Reported Speech_ datasets for who is speaking and who is being spoken to. Use the person data type for both extension terms. For example:

- `speaker:God` -- Find all places where reported speech is attributed to God.
- `addressee:God` -- Find reported speech marked as directed toward God.

#### Passage List

To search for citations of any references contained in a [Passage List](../Documents/passagelistdocument.md) document, use the PassageList search extension. The content of the term is the exact name of the Passage List.

For example:

- `passagelist:"My Favorite Inspirational Verses"` -- Finds any of the passages listed in the given Passage List.

> Note that the name of the Passage List has to match an existing document exactly. For best results, copy and paste the name of the document:


#### Headword

Search for [Headwords](../Glossary/headword.md) used to identify articles in dictionary-type resources (such as lexicons, encyclopedias, and concordances) using the  structure `headword:word`.

For example:

- `headword:trust` -- Returns results with entries titled "Trust."
- `scripture IN headword:trust` -- Finds "scripture" in entries titled "Trust."

#### Label

A label is a special data type that affixes a classifying name and a series of optional attributes and their values that further describe the properties or characteristics to a range of resource text. In many cases, the `label` tag is not needed.

Consider how Psalm 8 might be labeled:

Psalm / Attribution: David / Genre: Praise / Structure: Chiastic / Tags: Messianic, Superscription

"Psalm" in this example is the label name that classifies the text as a Psalm. The attributes (Genre, Structure, etc.) further describe the Psalm's characteristics.

Once such labels have been affixed to resource text, the Label extension allows for them to be searched by class name with optional constraints based on parameters within the label.

Add an attribute name to find labels that specify an attribute regardless of its value:

`psalm:genre:*`

Add an attribute value to further narrow results down to only Psalms in the praise genre:

`psalm:genre:Praise`

Label attribute constraints come in the form _attributeName operator attributeValue_. The attribute name is the name of the attribute to match against, for example `Attribution` or `Genre`. Label attributes have one or more values of a given type, so the _attributeValue_ specifies what value a given attribute must have.

Use `AND` to specify more constraints based on properties, for example, messianic praise Psalms attributed to David:

`psalm:(tag:Messianic AND genre:Praise AND attribution:David)`

For a list of all currently shipping labels and their attributes, see [Searchable Labels](../Searching/searchablelabels.md).


## Learn More

- [Search Help](http://wiki.logos.com/New_Search_HELP) -- User-maintained public wiki, Wiki.Logos.com

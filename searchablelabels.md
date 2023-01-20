---
title: Searchable Labels
id: searchablelabels
milestone: help.searchablelabels
---

# Searchable Labels

A label is a tag that editors have attached to a word, phrase, or section to identify it belongs with a particular class (e.g., Command, Prayer, Miracle). In addition to the class, labels indicate attributes of each labeled unit (e.g., Type, Theme, Instrument).

Each Label has a Class Name and multiple Attributes. An Attribute has a name and one or more values. The easiest way to identify a label is with the [Context Menu](../Resources/contextmenu.md) where label tags for the selected word appear in the left side of the panel.

The type of value used in the specified label search is notated below along with the syntax that is used to search it:

- `"..."` -- Indicates a plain text value such as `"Smith, John"`.
- `datatype:` -- Indicates a data type reference of a specified type such as `Bible:"John 3:16"`.
- `123` -- Indicates a numeric value.

Depending on the datasets in the user's library, the following labels can be used to search.


## Resource Labels

The following labels are typically found embedded directly into resources as part of the publication process. These labels are intended to present observable/intrinsic attributes of the articles that they are applied to in a straightforward manner. The list that follows is intended to be exhaustive.

Generally speaking, use [Label Entry](../Tools/labelentry.md) to extend these label sets to more resources in your library for your own use. 


### Bible Outline

Labels an outline of biblical text, especially in commentaries and Bible handbooks. These labels are used to populate the Outlines guide section, as well as the [Bible Outline Browser](../Interactives/bibleoutlinebrowserinteractive.md) interactive.

- `reference:bible:...` -- The passage range covered by the outline.

For example:

- `bibleOutline:reference:bible:"Romans 5–7"`


### Journal Article

Labels a single article in a journal resource. A search for this label populates the [Journals](../Guides/Sections/journalsguidesection.md) guide section.

- `title:...` -- The title of the article.
- `author:...` -- The list of article writers' names.
- `topics:topic:...` -- The list of topic data type references associated with the article.
- `references:datatype:...` -- The list of other associated data type references (mostly `bible:...`).
- `date:123` -- Date data type reference specifying publication data of the article.
- `editor:...` -- The list of article editors' names.

For example:

- `journalArticle:(references:bible:"Romans 5" AND topics:topic:Justification)`
- `journalArticle:(author:Goodrich AND date:2013)`


### Lectionary Reading

Lectionary resources consist of sets of readings (or “lessons”) to be read on particular occasions. Each reading has a title and a list of references. Lectionary Reading labels are used to precisely mark up the title and references for each reading in a lectionary resource. This populates the Lectionary section in the Dashboard of the [Home Page](../Home Page/homepage.md). 

> Note: Liturgical date is not currently included in these labels.

- `title:...` -- Refers to the kind of reading, such as "Old Testament" or "Gospel."
- `references:bible:...` -- A list of references contained in the reading.

For example:

- `label:("Lectionary Reading" AND references:bible:"Isaiah 60")`


### Personal Letter

Labels a letter from one person to another. A search for this label populates the "Letters" [Factbook](../Tools/factbook.md) section.

- `author:biography:...` -- Biography (notable person) data type reference of the person who wrote the letter. If the person is not in the notable people database, this will be plain text of their normalized name. For example, `personalLetter:author:biography:"C. S. Lewis"` and `personalLetter:author:"C. S. Lewis"` return the same results.
- `recipient:biography:...` -- Biography data type reference of the person who received the letter. If the person is not in the notable people database, this will be plain text of their normalized name.
- `date:123` -- Date data type reference of when the letter was sent, if known.
- `references:bible:...` -- Bible references associated with the letter, if any.
- `themes:preachingTheme:...` -- Sermon themes associated with the letter, if any.
- `place:...` -- The location from which or to which the letter was sent, if known.

For example: 

- `personalLetter:author:"C. S. Lewis"`


### Preaching Theme

Labels themes for use when preparing material to preach. These themes populate the [Theme](../Guides/Sections/themeguidesection.md) guide section.

Example:

- `preachingTheme:love`


### Sermon

Labels a single sermon in a collection of sermons. A search for this label populates the [Sermons](../Guides/Sections/sermonsguidesection.md) guide section.

- `creator:...` -- Creator is the normalized name of the person who developed and delivered the sermon.
- `title:...` -- Title is the name given to the sermon by its creator.
- `subtitle:...` -- Subtitle is the ancillary title information given by its creator.
- `series:...` -- The series in which the sermon was originally preached, if any.
- `references:bible:...` -- Bible references for the sermon as a whole.
- `date:123` -- When the sermon was first delivered.
- `liturgicalDate:123` -- Is typically the liturgical date when the sermon was first delivered.
- `themes:...` -- Themes associated with the sermon, if any.

For example:

- `sermon:(creator:Spurgeon AND references:bible:~"Romans 5")`
- `sermon:(creator:Keller AND references:bible:"Acts 2" AND date:1989)`


### Sermon Outline

Labels sermon outlines. A search for this label populates the [Sermon Outlines](../Guides/Sections/sermonoutlineguidesection.md) guide section.

- `creator:...` -- Creator is the normalized name of the person who developed the outline.
- `date:123` -- When the outline was created, if any.
- `liturgicalDate:123` -- Is typically the liturgical date associated with the sermon outline.
- `references:bible:...` -- Bible references for the outline as a whole.
- `series:...` -- The series in which the outline appears, if any.
- `themes:...` -- Themes associated with the outline, if any.
- `title:...` -- The name given to the outline by its creator.

For example:

- `sermonoutline:(themes:love AND references:"1 John 4:17–21")`


## Interactive Dataset Labels

The following labels are typically delivered as supplemental datasets that accompany or mirror interactives.


### Intertext Labels

The [dataset](https://ref.ly/logosres/cidbdocnoncanusebib?art=art8) behind the [New Testament Use of the Old Testament](../Interactives/ntuseofotinteractive.md) interactive identifies when one text directly relates to another. The Intertext label is comprised of:

- `corpus:...` -- A particular body of work.
- `relationship:...` -- Speaks to how the two texts are connected.
	- Citation -- An explicit reference to Scripture with a citation formula (e.g., “It is written,” or “the Lord says,” or “the prophet says”).
	- Quotation -- A direct reference to Scripture, and is largely matching the verbatim wording of the source but without a quotation formula.
	- Allusion --  An indirect but intentional reference to Scripture that is likely intended to invoke memory of the Scripture.
	- Echo -- A verbal parallel evokes or recalls a Scripture (or series of Scriptures) to the reader, but likely without authorial intention to reproduce exact words.
- `source:bible:...` -- A Bible reference. This can be a book, book and chapter, or a complete book-chapter-verse reference.
- `target:...` -- If used, the target is a reference in the corpus in question.

For example:

- `intertext:source:"Isa 40:3"` -- Finds New Testament passages with Isaiah 40:3 as the source.
- `intertext:target:"Mat 3:3"` -- Finds Old Testament passages with Matthew 3:3 as the target.
- `speaker:Jesus IN intertext:source:Genesis–Malachi` -- Finds Old Testament passages referenced by Jesus.


### Miracles of the Bible

The [dataset](https://ref.ly/logosres/fballmiracles?hw=Introduction) behind the [Miracles of the Bible](../Interactives/miraclesofthebible.md) interactive annotates miracle stories in the Old and New Testament. The Miracle label supports:

- `agent:person:...` -- The person or entity responsible for committing the miracle. Some miracles may have more than one miracle worker. In some cases the `person` tag is not needed.
- `audience:person:...` -- The named audience witnessing the miracle. If the audience is unnamed in the text, it is not annotated. In some cases the `person` tag is not needed.
- `beneficiary:person:...` -- The person or entity directly benefiting from the commission of the miracle. In some cases the `person` tag is not needed.
- `instrument:...` -- An item or thing directly used in the commission of the miracle. Not every miracle will specify an instrument. There may be zero or many.
- `type:...` -- Miracles have been classified as one of nine miracle types. A single miracle story may exhibit more than one type.
   - Affliction -- Miraculous events that cause physical ailments such injury, disease, or disability.
   - Communication -- Miraculous events that involve supernatural messages to a human audience.
   - Exorcism -- Miraculous events that involve the casting out of one or more demons from a person. Exorcisms may co-occur with healings.
   - Healing -- Miraculous events that result in the curing of injury, disease, or disability.
   - Judgment -- Miraculous events where the supernatural event functions as a punishment on an individual or group of people. Judgments may co-occur with other miracle types.
   - Nature -- Miraculous events that affect or disrupt the physical world.
   - Provision -- Miraculous events that result in the beneficiary having something they did not have previously.
   - Resurrection -- Miraculous events that cause a dead patient to be brought back to life.
- `patient:person:...` -- The person or thing directly affected by the miracle. In some cases, the `person` tag is not needed.
- `thingInvolved:thing:...` -- Items or things mentioned in the commission of the miracle. There may be zero or many. In many cases, the `thing` tag is not needed.
- `title:...` -- The title assigned to the miraculous event (e.g., "Jesus Feeds 5,000").

For example:

- `miracle:agent:Jesus` -- Find the miracles of Jesus.
- `miracle:(any:Peter)` -- Find every miracle involving Peter.
- `miracle:(agent:God AND type:provision)` -- Find where God miraculously provided for his people. 


### Measure

The [Measure Conversions dataset](https://ref.ly/logosres/cidbdocmeasconv?art=art4) adds labels on word-numbered Bibles for phrases identifying specific quantities measured with units of measure. This dataset powers the [Weights and Measures](../Interactives/weightsandmeasuresinteractive.md) interactive. Data is searchable with the label `measure` and the following attributes:

- `conversion:...` -- A localized text string, of which each label may have up to five showing a conversion of the quantity to other units. The converted units can be another ancient measure, metric or imperial units (e.g., cm, feet, kg, gallons, etc.), or money in US dollars or Euros.
- `number:123` -- The number used in the text (e.g., 3, 40, etc.).
- `substance:...` -- An optional field identifying a substance being measured, such as gold or silver. Omitted except for weights of metal having monetary value.
- `unit:...` --The unit of measure in the text (e.g., cubit, shekel, etc.).

For example:

- `measure:substance:Silver`


### Mitzvoth

The [Commandments of the Law](https://ref.ly/logosres/interactive:ot-commandments?pos=index.html) Interactive provides information on the 613 Mitzvoth (commandments) as delineated by Maimonides (Rambam) in the middle ages; perhaps in 1170 C.E. (Chavel, xi). These commandments are traditionally described as “The 613 mitzvoth of the Torah.”

- `applicableToday:...` -- This attribute is either `True` or `False`.
- `classification:...` -- Categories by which the commandments are organized, which include:
	- Administration of the Jewish State
	- Belief in God
	- Criminal Law
	- Cultivation of the Land
	- Duties to God
	- Duties Toward Family
	- Duties Toward Others
	- Financial and Interpersonal Duties
	- Food Prohibitions
	- Gifts, Sabbatical Year, and the Jubilee
	- Idolatry
	- Justice and the Courts
	- Prohibitions in Marriage
	- Property Laws
	- Sacrifices and Priestly Gifts
	- The Holy Days
	- The Jewish State
	- The Sabbath and Festivals
	- The Sanctuary and Sacrifices
	- Uncleanness and Purification
- `command:...` -- The content of the command.
- `number:123` -- The miztvoth number includes a P (positive) or N (negative) prepended to an index number. The 248 positive commandments are numbered sequentially from P1 to P248. The 365 negative commandments are numbered sequentially from N1 to N365.
- `state:...` -- This indicates whether the command is something one is obligated to do (`Positive`) or to not do (`Negative`).

For example:

- `mitzvoth:(classification:"Duties to God" AND applicableToday:True AND state:Negative)`


### Proverbs Browser Dataset

The [Proverbs Explorer](../Interactives/proverbsexplorerinteractive.md) divides Proverbs into several categories. [This dataset](https://ref.ly/logosres/cibdocproverb?art=art4) extends the markup to the Bible text. The Proverb label supports:

- `type:...` -- Which is the general classification of the Proverb, one of:
	- Advice -- Is predicated as a direct address, often to a specific hearer.
	- Characterization -- Is an attempt to define a class of persons by their characteristics.
	- Consequence --  Explains the consequence or result of certain behavior.
	- Means -- Defines the means by which something happens.
	- Ode to Wisdom -- Is the personification of Wisdom.
	- Prologue -- Introductory comments to a set of Proverbs.
	- Saying -- Is an assertion of a general truth.
- `form:...` -- The shape of the proverbial text, one of:
	- Antithetical Parallel -- Is where the second half rebuts the first.
	- Better/Than -- Is a comparison between one thing that is said to be better than another thing.
	- List -- Is an indivisible list of mostly similar parallel lines that form a single coherent thought.
	- Redirection -- Is when a problem is proposed and answered with an apparent _non sequitur_ to redirect the thinking posed by the problem.
	- Similar Parallel -- Where the second half restates the first half in other terms.
	- Simile -- Is an explicit comparison.
	- Statement -- Is a complete thought expressed only by both lines, which are not parallel.
	- Synthetic Parallel -- Where the second half builds on the first half.

For example:

- `proverb:(type:Advice AND form:"Similar Parallel")`


### Psalms Explorer Dataset

The [Psalms Explorer](../Interactives/psalmsexplorerinteractive.md) interactive annotates each Psalm with a number of categories. These labels extend that categorization to the Bible text itself. The Psalm label supports:

- `accordingto:...` -- In Psalm superscriptions, there is sometimes a phrase “according to ...” that may refer to a tune name.
	- ‘Alamoth (The Virgin)
	- ‘Almuth Labben
	- ’Ayyeleth Hashahar (The Doe of the Dawn)
	- Jeduthun	
	- Mahalath
	- Mahalath Le’annoth
	- Shoshannim (Lillies)
	- Shushan ’Eduth (Lily of the Testimony)
	- Tashheth (Do not Destroy)
	- The Gittith
	- The Nehiloth (The Flutes)
	- The Sheminith (The Eighth)
	- Yonath ’Elem Rehoqim (A Dove on Far-off Trees)
- `attribution:...` -- Who the Psalm is attributed to.
	- Anonymous
	- Anonymous (LXX)
	- Asaph
	- David
	- David (LXX)
	- Ethan the Ezrahite
	- Haggai (LXX)
	- Heman the Ezrahite
	- Korahites
	- Moses
	- Solomon
	- Zechariah (LXX)
- `genre:...` -- The kind of Psalm.
	- Hymn
	- Lament
	- Praise
	- Royal
	- Thanksgiving
	- Trust
	- Wisdom
- `structure:...` -- The poetic organization of the Psalm, which is one of the following :
	- Acrostic -- The first words of lines (or groups of lines) start with each letter of the alphabet in succession.
	- Chiastic -- Also called "onion" or "concentric" structure where earlier sections are rhymed thematically by later ones.
	- Strophic -- The Psalm is divided into strophes.
- `tag:...` -- Miscellaneous attributes of a Psalm. Among the more interesting tags:
	- Community
	- Imprecatory
	- Messianic
	- Penitential
	- Selah
	- Superscription
	- Zion

For example:

- `psalm:(attribution:David AND tag:Messianic AND genre:Lament)`
- `psalm:(attribution:Anonymous AND attribution:"David (LXX)")`
- `psalm:(accordingto:"The Sheminith (The Eighth)" AND structure:Strophe AND tag:Penitential)`


### Sacrifices

The [Feasts and Sacrifices](../Interactives/israelitefeastsandsacrificesinteractive.md) interactive visualizes the Israelite religious feasts in calendar form and annotates instances of sacrifices in the text of the Old Testament and New Testament. The data behind the interactive is searchable using the `sacrifice` label and the following attributes:

- `content:...` -- The substance being offered as the sacrifice.
- `offerant:...` -- The person or entity responsible for making the sacrifice.
- `purpose:...` -- The reason for which the sacrifice was made.
- `type:...` -- Sacrifices have been classified as one of thirty-one sacrifice types.
	- Baked
	- Blood
	- Burnt
	- Consecration
	- Contribution
	- Crucifixion
	- Drink
	- Food
	- Freewill
	- Gift
	- Grain
	- Guilt
	- Incense
	- Meal
	- Money
	- Offering
	- Other
	- Peace
	- Repentance
	- Riches
	- Sex
	- Sin
	- Smoke
	- Spiritual
	- Thank
	- Tithe
	- Votive
	- War-booty
	- Wave
	- Whole
	- Wood

For example:

- `sacrifice:purpose:Thanksgiving`


### Speaking to God

The [Speaking to God](https://ref.ly/logosres/interactive:speaking-to-god?pos=index.html0) interactive classifies reported speech with God or another person of the Trinity as the addressee. Searchable attributes include:

- `content:...` -- The content of the speech, classified as:
	- Affirmation
	- Blessing
	- Complaint
	- Confession
	- Consecration
	- Curse
	- Imprecation
	- Intercession
	- Lament
	- Oath
	- Other
	- Petition
	- Praise
	- Query
	- Repentance
	- Response
	- Thanksgiving
- `context:...` -- The biblical context in which the speech occurs, grouped by:
	- Communal
	- Incarnational
	- Literary
	- Other
	- Prophetic
	- Ritual
	- Solitary
	- Theophanic
	- Visionary
- `distance:...` -- Reports the proximity of the speaker to God in the following categories:
	- Abstract
	- Local
	- Remote
- `mode:...` -- The mode of speech
	- Address
	- Conversation
	- Meditation
	- Music
	- Other
	- Prayer
- `type:...` -- The type of speech
	- Dialogue
	- Monologue
	- Soliloquy

For example:

- `speech:(mode:music AND distance:local)`


## Biblical Annotation Datasets

The following labels are delivered by datasets that specifically mark up the Bible.


### Accent

The [Accents in the Greek New Testament dataset](https://ref.ly/logosres/cidbdocaccgknt?art=art2&off=71&ctx=Introduction%0a~This+dataset+uses+informati) uses information from Smyth’s _Grammar_ (cf. §§149–187) in its analysis of accents in the Greek New Testament. The text is searchable using the `accent` label and the following attributes:

- `name:...` -- Names include:
	- None -- No accents occur on any syllable.
	- Oxytone -- An instance of an acute accent on the ultima.
	- Paroxytone -- An instance of an acute accent on the penult.
	- Proparoxytone -- An instance of an acute accent on the antepenult.
	- Perispomenon -- An instance of a circumflex accent on the ultima.
	- Properispomenon -- An instance of a circumflex accent on the penult.
- `position:...` -- Integer noting position of the syllable in the active word. Positions include:
	- Antepenult -- Third to last syllable of the word.
	- Penult -- Next to last syllable of the word.
	- Ultima -- Last syllable of the word.
- `type:...` -- Individual accent in the word.
    - Acute ´
    - Grave ˋ
    - *Circumflex* ˆ

For example:

- `accent:type:Circumflex `


### Altar

The [Altars in the Bible dataset](https://ref.ly/logosres/fballaltars?hw=Introduction) annotates the entire Bible including all books in the Protestant canon along with the deuterocanonical books in other Christian traditions. The one limitation is that this resource covers all physical manifestations of altars and does not catalog figurative or archetypal references. This data is searchable using the label `altar` and the following attributes:

- `builder:...` -- An altar builder may be direct or proximate. For example, Abraham built altars directly; however, the Bible often speaks of the Israelites as building altars. These altars were built by representatives of the Israelites, but the Israelites are still listed as the builders.
- `event:...` -- An event is included where an altar is associated with an event; for example, Aaron built an altar on Sinai in relation to the Golden Calf event.
- `location:...` -- A location is provided for each altar with the location sometimes being general (e.g., the Land of Israel) and sometimes specific (e.g., the Temple of Solomon).
- `material:...` -- Altars were built of a limited set of materials: earth, stone, bronze, or some combination of those elements (i.e., stone overlaid with bronze).
- `purpose:...` -- While most altars were built generically for the purpose of sacrifice, sometimes those sacrifices were made for other purposes, like a covenant. These broader purposes are also listed here.
- `title:...` -- Title assigned to the altar.

For example:

- `altar:builder:Abraham`


### Battle

A battle consists of combat between two or more armed forces, typically fought as part of a larger conflict. The Bible contains many references to combat from large-scale wars to one-on-one combat where each side is represented by an individual combatant (e.g., David versus Goliath in 1 Sam 17:1–58). Instances where the fighting appears to be one-sided, such as in a raid or personal conflicts and disputes between individuals, were not included in the [Battles in the Bible dataset](https://ref.ly/logosres/fballbattles?hw=Introduction). The data is searchable using the label `battle` and the following attributes:

- `belligerent:...` -- Typically a people or political organization (e.g., Egyptians) or nation (e.g., Shinar) engaged in a conflict.
- `date:...` -- The year the combat event took place with a timeline link, where possible.
- `force:...` -- A named armed force or kind of armed force, if given. 
- `forceComponent:...` -- Number of fighters or kinds of fighters (e.g., cavalry) if given.
- `leader:...` -- Individuals mentioned in the text as leading one side or as military commanders of the armed forces.
- `location:...` -- The place where the combat event took place.
- `result:...` -- Details of what happened as a result of the battle and/or specifics on casualties.
- `thingInvolved:...` -- Limited to elements of a battle such as weapons or other things directly related to the combat event or its result.
- `title:...` -- Title assigned to the battle.
- `type:...` -- Where possible, battles have been classified as one or more of the following types:
	- Ambush -- A military attack utilizing the element of surprise.
	- Battle -- A combat event between two or more armed forces.
	- Civil War -- A war or conflict between forces from the same nation or political organization.
	- Siege -- A military blockade of a city or fortress.
	- War -- A prolonged military engagement consisting of multiple combat events. 
- `victor:...` -- Where given, the belligerent who won the battle, or sometimes a leader in the case of a Civil War.

For example:

- `battle:(type:Siege AND location:Jerusalem)`


### Benediction

_The Baker Encyclopedia of the Bible_ defines a benediction as “Pronouncement of God’s favor upon an assembled congregation.” The [Benedictions in the Bible dataset](https://ref.ly/logosres/fballbenedictions?hw=Introduction) uses this definition as a point of departure, widening the target of the benediction from an assembled congregation to a generic person or group that is the addressee of the utterance classified as a benediction. This dataset annotates instances of benedictions found throughout the Old Testament, deuterocanon/apocrypha, and New Testament. The data is searchable using the label `benediction` and the following attributes:

- `addressee:...` -- The entity to whom the benediction is addressed.
- `place:...` -- The location where the benediction occurs. This is an optional field.
- `speaker:...` -- The person or people who are giving the benediction.
- `title:...` -- A title assigned to the benediction.

For example:

- `benediction:speaker:Jesus`


### Burial

All burials reported in the Old Testament, deuterocanon, and New Testament have been annotated in the [Burials in the Bible dataset](https://ref.ly/logosres/fballburials?hw=Introduction). Burials are searchable using the label `burial` and the following attributes:

- `burialSite:...` -- Location of the burial.
- `causeofDeath:...` -- What caused the death of the person being buried.
- `event:...` -- Larger biblical context for the burial.
- `personBuried:...` -- The person or people being buried.
- `plotOwner:...` -- Person or people who owned the plot of land, where available.
- `region:...` -- The geographical region of the burial.
- `related:...` -- Topics related to the burial.
- `title:...` -- Title assigned to the burial.
- `tombKind:...` -- The kind of tomb used for the burial.

For example:

- `burial:tombKind:Cave`


### Cantillation

The [Cantillation Analysis Dataset](https://ref.ly/logosres/cidbdoclexhebbib?art=art4) uses the label `cantillation` and annotates up to three attributes per mark. The label information is indexed at the word level and the attributes include:

- `name:...` -- The name of the mark. The naming system used by the [Hebrew Cantillations](../Interactives/hebrewcantillationsinteractive.md) Interactive is used in the cantillation analysis in order to be consistent.
- `rank:...` -- If the mark is disjunctive, it implies a rank in the text. This rank is used to build the hierarchy. If the text is prose, the available ranks are `"High Emperor"`, `Emperor`, `King`, `Duke`, and `Officer`. If the text is poetry (Job, Psalms, Proverbs) then the available ranks are `Emperor`, `King`, `Duke`, and `Officer`.
- `type:...` -- Available types are `Disjunctive` and `Conjunctive`.

For example:

- `cantillation:(rank:"High Emperor" AND type:Disjunctive)`


### Command

The [Commands in the Bible dataset](https://ref.ly/logosres/cidbdoccmdbible?art=art5) provides an annotation of all the commands in the Bible based on the underlying original language. The data is searchable using the label `command` and the following attributes:

- `type:...` -- Command types include:
	- Advice
	- Command
	- Curse
	- Invitation
	- Offer
	- Permission
	- Prohibition
	- Request
	- Warning
	- Well-wish
	- Wish
- `verbClass:...` -- The semantic category of the command verb. See the [dataset documentation](https://ref.ly/logosres/cidbdoccmdbible?art=art41) for a complete list.

For example:

- `command:(type:Command AND verbClass:Existence)`


### Covenant

The [Covenants in the Bible dataset](https://ref.ly/logosres/fballcovenants?hw=Introduction) annotates instances of covenants found through the Old Testament, Deuterocanon/Apocrypha, and New Testament. The data is searchable using the label `covenant` and the following attributes:

- `beneficiary:...` -- Individuals or groups who received benefits of the covenant.
- `condition:...` -- The stipulations regarding the covenant that must be met by one or both parties.
- `consequence:...` -- The results or actions taken if the covenant is broken.
- `giver:...` and `receiver:...` -- The two parties who made the covenant together. This is the only information each covenant requires.
- `mediator:...` -- Occasionally, a covenant was mediated by a third-party.
- `place:...` -- The location where the covenant was made.
- `promise:...` -- The content or agreement of the covenant, that which is promised by one or both parties.
- `sign:...` -- Occasionally, a visible sign was given to affirm the covenant.
- `title:...` -- A title for the covenant.

For example:

- `covenant:sign:Rainbow`


### Daily Event

The Today in Christian History dataset is searchable using the label `dailyEvent` and the following attributes:

- `concepts:...`
- `date:...`
- `people:...`
- `places:...`
- `timeline:...`
- `title:...`
- `type:...`

For example:

- `dailyEvent:date:"March 1274"`


### Famine

The [Famines in the Bible dataset](https://ref.ly/logosres/fballfamines?hw=Introduction) compiles information on all the famines described in the Bible, whether based on climate, warfare, or other factors. Famines are searchable with the label `famine` and any of the following attributes:

- `affected:...` -- Those who were affected by the famine.
- `cause:...` -- The cause of the famine.
- `consequence:...` -- The consequences of the famine relative to the biblical narrative.
- `duration:...` -- How long the famine lasted.
- `event:...` -- The biblical event connected to this famine.
- `location:...` -- Where the famine took place.
- `mention:...` -- Other Bible passages that mention this famine.
- `period:...` -- The period of biblical history in which the famine occured.
- `title:...` -- A title for the famine event.

For example:

- `famine:(period:"Patriarchal Age" AND mention:"Ps 105:16")`


### Fast

The [Fasts in the Bible dataset](https://ref.ly/logosres/fballfasts?hw=Introduction) examines the Bible (the Protestant canon along with the deuterocanonical books in other Christian traditions) and identifies texts directly related to the practice of fasting. The data was gathered by mining the indexes of many different sources related to fasts. The data is searchable using the `fast` label and the following attributes:

- `duration:123 Days` -- The length of a fast with common lengths being one day or forty days. A length of time is not always discernible. 
- `event:...` -- The primary event associated with the fast. An event is not always identifiable in texts like Psalms.
- `faster:...` -- The person or people group abstaining from food and sometimes also water.
- `location:...` -- The place where the fast occurs. 
- `proclaimer:...` -- The person who imposes a fast on a faster. A proclaimer is not always present as sometimes people engage in fasts of their own volition. 
- `reason:...` -- The purpose for which people engage in a fast, such as for victory in battle or to seek forgiveness.
- `title:...` -- Title assigned to the fast.

For example:

- `fast:duration:"40 Days"`


### Figurative Language

Instances of figurative language (metaphors, similes, and so on) in the Bible are marked with specific attributes. Values for the `Term` and `Type` label attributes are too numerous to list here. Consult the [Lexham Figurative Language of the Bible Glossary](https://ref.ly/logosres/lxfiglanggloss?art=article.1.1.3) for full details.

- `category:figurativeLanguageCategory:...` -- The broad category of the figure. The `figurativeLanguageCategory` data type takes a top-level category, and optional subcategories:
  - `Dysphemism`
  - `Euphemism`
  - `Hyperbole`
  - `Idiom`
  - `Metaphor`
	 - `Image`
	 - `Ontological`
	   - `Container`
	   - `Entity`
	   - `Objectification`
	   - `Personification`
	   - `Substance`
	 - `Orientational`
     - `Structural`
  - `Metonymy`
  - `Simile` -- subcategories: `Broad`, `Narrow`
  - `Symbolism` 
- `source:figurativeLanguageTerm:...` and `target:figurativeLanguageTerm:...` -- One of the referents (or domains) involved in expressing the figure. 
	- In "I am the good shepherd," both "Jesus" and "shepherd" are terms.
- `type:figurativeLanguageType:...` -- The unique combination of source term and target term create a "type". 
	- In "I am the good shepherd," the type is `Shepherd as Jesus`. 

For example:

- `figurativeLanguage:(category:figurativeLanguageCategory:"Metaphor, Ontological, Entity" AND source:figurativeLanguageTerm:Shepherd AND target:figurativeLanguageTerm:Jesus AND type:figurativeLanguageType:"Shepherd as Jesus")`

> Pro tip: Create a [Visual Filter](../documents/visualfilterdocument.md) document with `figurativeLanguage:*` as the search term and assign a distinctive style. This will highlight everywhere figurative language is used in a resource on the Visual Filters menu. 


### Bullinger's Figures of Speech

This dataset ships a bundle of Figure of Speech labels that mirror information found in _[Figures of Speech Used in the Bible](https://ref.ly/logosres/bullfig?ref=Page.p+xvii&off=11080)_ by E. W. Bullinger. If (and only if) a verse is mentioned in Bullinger's discussion of a figure of speech, that verse is labeled with that figure of speech. Each label supports:

- `name:...` -- Where the title name of the figure appears (e.g., “Zeugma” or “Aposiopesis”).
- `description:...` -- Is the short gloss for the figure (e.g., “Unequal Yoke” or “Sudden-Silence”).

For example:

- `figureofSpeech:name:Ellipsis`


### Killing

All the killings in the Bible have been annotated with the [Killings dataset](https://ref.ly/logosres/fballkillings?hw=Introduction). The data can be searched using the `killing` label and the following attributes:

- `event:...` -- The biblical event that provides the context.
- `instruments:...` -- The weapon(s) or instrument(s) used.
- `location:...` -- Where the killing occurred.
- `perpetrators:...` -- The person or people responsible.
- `title:...` -- The title assigned to the killing.
- `type:...` -- Available types include:
	- Assassination -- The killing of a person of high standing, usually for political reasons.
    - Battle defeat -- A death that happened as the outcome of war.
    - Capital punishment -- A killing at the behest of the state or a community.
    - Conquest -- Deaths that happen in the midst of one nation conquering another.
    - Conspiracy -- A killing via conspiracy.
    - Divine punishment -- A killing that happens by the hand of God or his messengers.
    - Fratricide -- The killing of one’s brother or sister.
    - Human sacrifice -- The sacrifice of human beings.
    - Involuntary manslaughter -- The negligent or accidental killing of one or more people.
    - Murder -- Intentional homicide.
    - Patricide -- The murder of one’s father.
    - Regicide -- The murder of a monarch.
    - Suicide -- Death by one’s own hand.
    - Vengeance -- Killing a person to avenge a wrong done to someone.
- `victims:...` -- The person or people killed.

For example:

- `killing:perpetrators:person:"Saul (king)"`


### Longacre Genre

Using a system defined in _The Grammar of Discourse_ by Robert E. Longacre, this dataset outlines four main genres---each having two sub-genres. See more details in the [Longacre Genre Analysis of the Bible Dataset Documentation](https://ref.ly/logosres/cidbdoclgenre).

- `primary:longacreGenre:...` -- The primary category.
- `secondary:longacreGenre:...` -- The subcategory.

Examples:

- `label:("Longacre Genre" AND primary:longacreGenre:"Behavioral: Evaluation" AND secondary:longacreGenre:"Expository: What things are or were like")`
- `section:longacreGenre:="Narrative: Story"`


### Marriage

All the marriages in the Bible have been annotated with the [Marriages datset](https://ref.ly/logosres/fballmarriages?hw=Introduction). The dataset can be searched using the label `marriage` and the following attributes:

- `context:...` -- The larger context or events surrounding the marriage.
- `event:...` -- A Timeline event.
- `husband:...` -- The name of the husband.
- `husbandNationality:...` -- The husband’s people group or country of origin.
- `location:...` -- The place where the marriage occurred.
- `title:...` -- Title assigned to the marriage.
- `wife:...` -- The name of the wife.
- `wifeNationality:...` -- The wife’s people group or country of origin.

For example:

- `marriage:husband:person:David`


### Meal

The [Meals in the Bible dataset](https://ref.ly/logosres/fballbanquets?hw=Introduction) annotates instances of shared meals found in the text of the Old Testament and New Testament. Shared meals found in the deuterocanonical and apocryphal books are also annotated. The text may refer to these meals as “feasts,” though these are to be distinguished from the religious feasts observed by the Israelites as part of following the law. This data is searchable with the `meal` label and the following attributes:

- `drink:...` -- Drinks served at the meal.
- `food:...` -- Food served at the meal.
- `guest:...` -- Guest(s) of the meal.
- `host:...` -- Host(s) of the meal.
- `location:...` -- Location of the meal.
- `occasion:...` -- The occasion of the meal (required). See the [dataset documentation](https://ref.ly/logosres/fballbanquets?hw=Appendix%3a+Meal+Occasions) for a complete list of meal occasions.
- `title:...` -- The title assigned to the meal (e.g., "Melchizedek and Abraham").

For example:

- `meal:occasion:celebration`


### Messianic Prophecy

The [Messianic Prophecy dataset](https://ref.ly/logosres/cidbdocmessproph?art=art4) annotates specific New Testament and Old Testament passages that meet the criteria outlined in the dataset documentation. Searchable attributes include:

- `content:...` -- A sentence indicating the nature of the fulfillment.
- `fulfillment:...` -- One of the following labels indicating how the New Testament writer indicates the prophecy has been fulfilled:
	- `"Author Proclamation"` -- The NT author makes an explicit claim about who fulfills the prophecy.
	- `Implication` -- The author cites the prophecy in a way that makes the fulfillment implicit.
	- `"Participant Proclamation"` -- One or many of the narrative participants makes an explicit claim about who fulfills the prophecy.
	- `Self-proclamation` -- The speaker makes a claim that they fulfill the prophecy themselves.
- `relationship:...` - The relationship between the Old and New Testament passages.
- `source:...` -- The Old Testament passage cited.
- `target:...` -- The New Testament passage cited.

For example:

- `messianicProphecy:(fulfillment:Self-proclamation AND source:"Isa 53:12")`


### Oaths and Vows

Oaths and vows recorded throughout the biblical text, powered by the [All the Oaths and Vows in the Bible Dataset](https://ref.ly/logosres/fballvows?hw=Introduction).

- `addressee:...` -- The person towards whom the oath or vow is directed.
- `event:...` -- The primary event associated with the speech act is given where possible.
- `location:...` -- A location is provided for each speech act, where possible. Sometimes a best estimation is made based on the surrounding context.
- `reason:...` -- A reason is provided for all but the most generic of vows.
- `speaker:...` -- The person who performs the speech act. In the case of prophecy, God is usually recorded as the speaker, not the prophet relating a message.
- `title:...` -- Each instance is categorized as either an oath or vow based largely on the distinguishing features noted in the _Lexham Bible Dictionary_ and _Lexham Theological Wordbook_.

For example:

- `oath:(reason:Battle AND speaker:David)`
- `vow:speaker:David`


### Parable

The [Parables of the Bible dataset](https://ref.ly/logosres/cidbdocparabib?art=art4) isolates every biblical parable as a Bible reference range. Each parable has been labeled with the following attributes:

- `audience:...` -- The audience the parable was related to.
- `speaker:...` -- The person responsible for relating the parable.
- `title:...` -- A title for the parable.
- `type:...` -- The type of parable. The following types are supported:
	- Instruction
    - Promise
    - Rebuke
    - Warning

For example:

- `parable:(type:warning AND speaker:Jesus)`


### Prayer

The [Prayers of the Bible dataset](https://ref.ly/logosres/fballprayers?hw=Introduction) annotates instances of prayers found throughout the Old Testament, deuterocanon/apocrypha, and New Testament.

- `addressee:...` -- The entity to whom the prayer is addressed.
- `content:...` -- The content of the prayer. Pryaer contents include:
	- Affirmation -- Expression of agreement.
    - Blessing -- Uses the formula “bless/blessed.”
    - Complaint -- Report of a specific grievance.
    - Confession -- Confession of faith; the speech act portion of salvation.
    - Consecration -- A kind of oath where one is set apart for divine service.
    - Curse -- Uses the formula “curse/cursed.”
    - Imprecation -- Request for justice or vengeance to come down on another.
    - Intercession -- Request on behalf of another.
    - Lament -- Expression of negative emotion.
    - Oath -- A promise, vow, covenant, or other swearing.
    - Petition -- Request for a specific consideration for oneself.
    - Praise -- Ascribing glory, adoration, worship, or recounting good deeds.
    - Query -- Request for information or direction.
    - Repentance -- Confession of sin, the speech act portion of repentance.
    - Thanksgiving -- An expression of gratitude.
    - Other -- Not otherwise categorized.
- `context:...` -- The context of the prayer. Prayer contexts include:
	- Communal -- Non-liturgical public expression.
	- Literary -- Speech to God used as a literary or rhetorical device.
    - Prophetic -- A non-visionary oracular experience.
    - Ritual -- Part of a ritual, cultic, or other religious exercise.
    - Solitary -- Personal prayer or music expressed in private.
    - Theophanic -- A dialogue with a manifested presence of God.
    - Other -- Not otherwise categorized.
- `place:...` -- The location where the prayer occurs.
- `speaker:...` -- The person (or people) who is praying.
- `title:...` -- The title assigned to the prayer, where applicable.

For example:

- `prayer:(speaker:"Jacob (son of Isaac)" AND context:Solitary)`


### Prepositional Phrase

The [Greek Grammatical Constructions dataset](https://ref.ly/logosres/cidbdocgkgram?ref=GrammaticalConstructions.incorp&off=1762&ctx=one.%0a%E2%80%A2+Object+Lemma%3a~+A+lemma+reference+) provides Logos users with better access to grammatical constructions which are of interest to both the exegete and the grammarian. Grammatical Constructions data track prepositional phrases in Greek with three different data points. These data points include the preposition, the object of the preposition, and where applicable, the case of the object of the preposition.

- `objectCase:...` -- An English word noting the morphological case of the object of the prepositional phrase. If the word has no case value (e.g., is an infinitive verb) the case will be stated as None. Cases include:
	- Accusative
	- Dative
	- Genitive
	- Nominative
	- Vocative
- `objectLemma:lemma.g:...` --  A lemma reference.
- `prepositionLemma:lemma.g:...` --  A lemma reference.

For example:

- `prepositionalPhrase:(prepositionLemma:lemma.g:=κατά AND objectCase:Accusative)`


### Promise

The [Promises in the Bible dataset](https://ref.ly/logosres/cidbdocpromise?art=art5) is an extension of the Sentence Types of the Old Testament, Speech Acts of the Old Testament, Sentence Types of the New Testament, and Speech Acts of the New Testament datasets. Searchable attributes include:

- `fulfillment:...` -- The way in which the promise was fulfilled.
- `theme:...` -- The theme associated with the promise.
- `verbClass:...` -- VerbNet categories characterizing the promise. See the Appendix of the [dataset documentation](https://ref.ly/logosres/cidbdocpromise?art=art11) for a complete list of `verbClass` options.


For example:

- `promise:theme:Covenant`


### Prophets, Priests, Regents, and Judges

The [Prophets, Priests, Regents, and Judges dataset](https://ref.ly/logosres/cidbdocprophpriest?art=art5) labels instances of people fulfilling these particular roles in the Bible. 

- `prophet:...`
	- `agent:...` -- The person annotated as a prophet.
	- `deity:...` -- The divine entity the prophet serves. Most prophets in the Bible are prophets of God but there are others mentioned in the text.
- `priest:...` 
	- `agent:...` -- The person annotated as a priest.
	- `deity:...` -- The divine entity the priest serves. Most priests in the Bible are priests of God, but there are others mentioned in the text.
	- `role:...` -- The context-specific role filled by the priest. Roles include:
		- Chief Priest
		- High Priest
		- Priest
- `regent:...` 
	- `agent:...` -- The person annotated as a regent.
	- `region:...` -- The context-specific region administered by the regent.
	- `role:...` -- The context-specific role filled by the regent. Roles include:
		- Emperor
		- King
		- Queen
		- Tetrarch
- `judge:...` 
	- `agent:...` -- The person annotated as a judge.
	- `region:...` -- The context-specific region administered by the judge.

For example:

- `regent:(role:queen AND region:"Egypt (nation)")`
	

### Question

The [Questions in the Bible dataset](https://ref.ly/logosres/cidbdocqsbible?art=art3) provides an annotation of all the questions in the Bible based on the underlying original language. The question label types include:

- `rhetorical:...` -- Labels questions as rhetorical or not. This label accepts either `true` or `false` entries.
- `type:...` -- Specifies the type of question. Question types include:
	- `Cause` -- A questioner asks what event led to a particular action, event, or state of affairs.
	- `Comparison` -- A questioner asks how one thing is similar to or different from another.
	- `Consequence` -- A questioner asks concerning the consequences of an event or action (i.e., “What then?”; “What now?”; etc.).
	- `Definition` -- A questioner asks what something means.
	- `Description` -- A questioner asks about the qualities of a person or thing.
	- `Expectation` -- A questioner asks why some expected event or action has not taken place.
	- `Explanation` -- A questioner asks for an explanation of some event, action, or state of affairs and what consequences it may have.
	- `Goal` -- A questioner asks about the motivation for an action.
	- `Instrument` -- A questioner asks what instrument or procedure someone will use to accomplish a goal.
	- `Means` -- A questioner asks what enables a person to do something.
	- `Opinion` -- A questioner asks someone’s opinion, whether official (e.g., a legal decision) or unofficial, concerning some advice or idea.
	- `Quantity` -- A questioner asks concerning the quantity of a variable (e.g.,“How much/many?”; “How long?”; etc.).
	- `Request` -- A questioner issues a request or command in the form of a question.
	- `This/that"` -- The questioner asks whether one thing or another is the case.
	- `Wh-` -- A questioner asks what person, place, thing, or time fills a given role (i.e., “Who?”; “What?”; “When?”; “Where?”; etc.).
	- `Yes/no` -- A questioner asks whether something is or is not the case.

For example:

- `question:type:Wh- AND speaker:God`


### Song

The [Songs in the Bible dataset](https://ref.ly/logosres/fballsongs?hw=Introduction) examines the Bible (the Protestant canon along with the deuterocanonical books in other Christian traditions) to identify songs and important categories of data associated with them. Every song has been labeled with the following information:

- `event:...` -- The event that provides the context for the song where it is possible to determine it.
- `instrument:...` -- Musical instruments used in the song’s performance.
- `singer:...` -- Person or people who sang the song.
- `speechAct:...` -- Often the purpose behind the song, such as praise, lament, or thanksgiving.
- `title:...` -- Title assigned to the song, such as “The Song of Moses” (Exod 15:1-18).

For example:

- `song:(speechAct:Praise AND singer:David)`


### Source Criticism

The data collated in the [Source Criticism dataset](https://ref.ly/logosres/cidbdocsourcrit?art=art4) has been curated by specific source critics. $ProductShort$ has utilized the analysis of these authors and created searchable data based on their analysis. The data is thus organized by the original creator of the analysis.

- `critic:Eissfeldt` -- To date, the only data curated originated with Otto Eissfeldt.
- `source:...` -- One of the following five sources:
	- `E` -- Texts which refer to God with the generic term *elohim*.
	- `D` -- Texts which refer to a source (or author) associated with Deuteronomy.
	- `J` -- Texts which explicitly use the divine name.
	- `L` -- Texts centered around the duties of lay Israelites.
	- `P` -- Texts which refer to the rights of the priesthood.

For example:

- `sourceCriticism:(source:P AND critic:Eissfeldt)`


### Supernatural Being

Relevant information from the [Angels, Demons, and Deities dataset](https://ref.ly/logosres/cidbdocangdemdeities?art=art4) can be searched using the `supernaturalBeing` label, followed by one or more of the following attributes:

- `location:...` -- Enter a location associated with the spiritual being.
- `name:...` -- The _Bible Knowledgebase_ entity.
- `type:...` -- Identifies the spiritual being as one of: `angel`, `demon`, `deity`, or `other`.

For example:

- `supernaturalBeing:(type:angel AND name:Gabriel)`


### Syllable

Relevant information about [Syllables in the Greek New Testament](https://ref.ly/logosres/cidbdocsyllgknt?art=art4) can be searched using the following fields:

- `count:123` -- Integer noting the total number of syllables in the active word.
- `grapheme:...` -- An individual syllable in the word.
- `graphemes:...` -- Each syllable in the active word, separated by a dash.
- `position:123` -- Integer noting position of the syllable in the active word.

For example:

- `syllable:(grapheme:=ψυ AND position:2 AND count:3)`


### Theophany

A theophany is a physical, visual, or audible manifestation of God in his full glory and power. The [Theophanies dataset](https://ref.ly/logosres/cidbdoctheophany?art=art4) is a complete annotation across both the Old and New Testaments. Due to the complete coverage, manifestations of every person of the Trinity are recorded. So, while Christophanies are traditionally considered a subset of Theophanies, they are included here.


- `time:...` -- The time of the theophanic event according to the narrative time. The labels are `past`, `present`, and `future`. Instances labeled as "Past" are those where theophanic events are remembered. Those labeled "Future" are events which are prophesied to happen in the future.
- `beholder:...` -- The audience of the theophanic event.
- `agent:...` -- The person of the Trinity who makes the theophanic appearance.
- `manifestation:...` -- How God manifests in the physical realm.
- `appearance:...` -- The physical form God uses in the manifestation. If there is no form specified, the label is set to Unknown.

For example:

- `theophany:agent:Jesus`


### Turning Point

The [Turning Points dataset](https://ref.ly/logosres/fballconversions?hw=Introduction) annotates turning points in the Old Testament, deuterocanon, and New Testament. A turning point is a broad concept that includes a religious experience in a person’s, or group of people’s, life. The experience leads the person or group to make a positive change in their actions or beliefs.

- `converted:...` -- Person or people who experience the turning point.
- `event:...` -- The larger event providing the context for the turning point.
- `proselytizers:...` -- The person or people responsible for the turning point.
- `relatedConcept:...` -- Topic or concept associated with the turning point.
- `religiousExperience:...` -- Type of experience characterized by the turning point (i.e., "following God's commands").
- `title:...` -- Title assigned to the turning point.

For example:

- `turningPoint:*` -- Finds all of the turning points in the Bible.


### Visions

Every instance of dreams and visions in the Old Testament, New Testament, and Apocrypha are annotated in the [All the Dreams and Visions in the Bible Dataset](https://ref.ly/logosres/fballvisions?hw=Introduction).

- `description:...` -- A brief summary of what was seen in the dream or vision.
- `event:...` -- A brief summary of what happened leading up to the dream or vision.
- `eventContext` -- Important information about the event that provides the immediate context for the vision or dream is recorded here.
- `interpretation:...` -- The meaning of the dream or vision as explained by an interpreter or the seer.
- `interpreter:...` -- Someone who explains what the dream or vision means.
- `location:...` -- The location of the seer at the time of the dream or vision.
- `message:...` -- A verbal or written communication within the dream or vision relaying important information or a directive to the seer.
- `outcome:...` --  Events or information related to whether any action was taken in response to what was seen or directed.
- `participantSeen:...` -- Person that appears in the dream or vision.
- `seer:...` -- The person who experiences the dream or vision.
- `setting:...` -- The location seen in the dream or vision, which is often different from the location of the seer at the time of the dream or vision.
- `thingSeen:...` -- Thing that appears in the dream or vision.
- `time:...` -- The time of day during which the dream or vision occurs.
- `title:...` -- Title assigned to the dream or vision.
- `type:...` -- The occurrence is identified as a dream or a vision. In a few cases, the occurrence is classified as both a dream and vision based on the description given in the textual reference.

For example:

- `vision:* INTERSECTS (afraid OR fear)` -- Finds all visions that also contain the words "afraid" or "fear."


### Wordplay

The [Wordplay Dataset](https://ref.ly/logosres/fbwordplay?art=introduction) annotates instances of wordplay across the Hebrew Bible and the Greek New Testament in an attempt to display the literary and linguistic creativity of the Bible. The instances of wordplay collected in this dataset all deal with the phonetic aspect of language. That is, there is some similarity or contrast in sound between several words in a text. This dataset categorizes thirteen different types of wordplay.

- `type:...` -- Enter one of the following types of wordplay to search the open Bible(s) for every instance.
	- `acrostic` -- A literary device that is based on visual representation.
	- `alliteration` -- The repetition of one or multiple consonants across a span of text.
	- `anagram` -- A literary device that repeats all the letters of another word in a different order.
	- `assonance` -- The repetition of one or multiple vowels across a span of text. Assonance is not as common in Hebrew wordplay as it is in Greek.
	- `"homonymic parallelism"` -- A specific type of alliteration and assonance where multiple words that have the same form, but differing derivations, are repeated across a span of text.
	- `"ironic wordplay"` -- A literary device where the reader’s/hearer’s expectations are subverted.
	- `"lemma parallelism"` -- A specific type of alliteration and assonance where multiple words that possess the same root are repeated across a span of text.
	- `hendiadys` -- A literary device that pairs words with similar semantic domains. The pair of words usually convey a single concept.
	- `parasonance` -- A specific type of alliteration and assonance where multiple words that differ in a single root letter are repeated across a span of text.
	- `pun` -- A literary device where an unexpected word or sense of a word is used in place of an expected one. The word that is used in place of the expected word sounds similar to the one that is replaced.
	- `rhyme` -- A literary device where the final sound of a word is repeated across a span of text.
	- `homoeoprophoron` -- A literary device where the initial sounds of a word are repeated across a span of text. The repeated sounds are a combination of consonant and vowel sounds.
	- `homoioteleuton` -- A literary device where the final sounds of a word are repeated across a span of text. The repeated sounds are a combination of consonant and vowel sounds.

For example:

- `wordplay:type:rhyme INTERSECTS speaker:Jesus`

## Other Datasets

The following labels are delivered by various datasets. They tend to mark new editorial content or value-added markup (i.e., information that is not already intrinsically present in the text being labeled or available as part of another dataset or interactive).


### Bible Questions and Answers

The Bible Questions and Answers supplemental dataset provides answers to questions posed in [All Search](../Searching/allsearch.md). These questions and answers also appear in [Factbook](../Tools/factbook.md), and can be searched using the `answer` label and the following attributes:

- `question:...` -- The text of the question.
- `reference:...` -- Bible reference.
- `topic:...` -- Topic reference
- `theme:preachingtheme:...` -- Preaching Theme reference.
- `other:...` -- A data type reference representing a data type not listed above.

For example:

- `answer:topic:Salvation`


### Bible Books Supplemental Dataset

The [Bible Books Supplemental Dataset](https://ref.ly/logosres/cidbdocbibguide?art=art2) delivers several labels. These labels are applied to books throughout the library, and are used to populate the Bible Book Guides section in the [Factbook](../Tools/factbook.md).

- `"Additional Information"` -- Populates the `~See Also` section.
- `Background` -- Situational, social, and historical context of the book.
- `Canon` -- Canonicity (reception throughout church history), historicity, and authenticity of the book.
- `Content` -- High-level discussions of the material in the book.
- `Form` -- Unity, composition, style, and structure of the book.
- `Meaning` -- Theme, emphasis, interpretation, theology, and message of the book.
- `Objects` -- Geography and key figures of the book.
- `Origin` -- Authorship, date, and purpose of the book.

These labels all support two attributes:

- `reference:...` -- Biblical reference specifying the biblical book under discussion.
- `subcategory:...` -- The Bible Book category and sub-category that the text belongs to.

For example:

- `label:(Origin AND reference:Deuteronomy)`
- `label:(Meaning AND reference:Philippians)`


### Semantic Feature

These Semantic Feature labels ship as part of the Propositional Outlines ([Old](https://ref.ly/logosres/cidbdlexpropoutot?art=art4) and [New](https://ref.ly/logosres/cidbdoclexoutnt?art=art4) Testament) datasets. They are used to reformat the Bible text into a propositional outline using the Propositional Outline visual filter.

- `propositionalOutline:...` -- The name of the kind of proposition.

For example:

- `propositionalOutline:=Affirmation`

> For a complete listing of searchable propositions, see [The Lexham Propositional Outlines Glossary](https://ref.ly/logosres/lxhmsmntcglssry?art=title).


### Sentence Types

Types of sentences are annotated with the `Sentence` datatype. Consult [Sentence Types: Dataset Documentation](https://ref.ly/logosres/cidbdocsenttype) for full details.

Example:

- `sentence:"Interrogative Sentence"` -- To find all the questions.


### Speech Acts

The _Speech Acts Dataset_ is designed to annotate sentences in an attempt to capture the volition or intent of the speaker/writer. Consult [Speech Acts Dataset Documentation](https://ref.ly/logosres/cidbdocspeechact) for full details.

Example:

- `section:speechAct:="Obligative: Directive"` -- Finds all the obligative directives (i.e., where the speaker tries to get the hearer to do something).
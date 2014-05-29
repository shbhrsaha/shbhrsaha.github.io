---
layout: post
title: Polly want to write a limerick
---

![](/static/polly-limerick/polly_screenshot.png)

### Limericks Follow Patterns
I've been reading lately about how computer scientists are researching the art of jokes. They're asking the question, "What makes a joke funny?", and writing programs that come up with their own jokes.

Over the course of this reading, I stumbled upon [these lists of English words](http://wordlist.sourceforge.net/). In particular, the "Part Of Speech Database" caught my interest.

Putting two and two together, I thought I'd give auto-generated jokes a shot. I wanted to make something super-simple, not requiring advanced NLP. Limericks fit the bill decently well. These short, rhyming poems follow a consistent structure that depends largely on part of speech and rhyme.

> I know a man with a hairy leg <br />
> who takes his drinks with some dairy keg. <br />
> Then one day I saw <br />
> his head under a claw. <br />
> I screamed, "Oh! Does, anyone have a scary egg?"

Polly is a Python script I wrote that takes the part of speech database and a limerick template as input, and generates rhyming limericks that match the template.

### How Polly Works
Here's how an example template file looks:

> I know a man with a @A !N <br />
> who takes his drinks with some @A !N. <br />
> Then one day I saw <br />
> his head under a claw. <br />
> I screamed, "Oh! Does, anyone have a @A !N?"

As you'll notice, this is the template for the limerick presented earlier, but some of the rhymes have been replaced with 2-character sequences of a special character followed by a letter.

Matching special characters signify matching rhymes. For example, hairy, dairy, and scary all correspond with the @ symbol because they rhyme. Likewise, leg, keg, and egg correspond with the ! symbol.

The letter after the symbol signifies the part of speech. The @ words are all adjectives (A) and the ! words are all nouns (N). The POS abbreviations follow the conventions described in the part of speech database. Here's a sample:

- N: Noun
- V: Verb
- A: Adjective
- v: Adverb

Polly works by processing the part of speech database to group words with common endings-- this is a rudimentary way to craft rhymes. Then, the script parses the limerick template and replaces the 2-character sequences with words from the database that match rhyme and part of speech.

### Generated Limericks
The results are quite amusing, most of the time meaning rubbish. Here's a selection of the limericks it generated:

> Mary had a little certification. <br />
> She also had a restimulation. <br />
> I've often seen her little syllabication, <br />
> But I've never seen her perambulation. 

> I know a man with a cheek severance <br />
> who takes his drinks with some sleek endurance. <br />
> Then one day I saw <br />
> his head under a claw. <br />
> I screamed, "Oh! Does, anyone have a Greek insurance?"

### Github
Try it out yourself! You can download Polly and all the instructions you need from [Github](https://github.com/shbhrsaha/polly/).

[ March 2013 ]
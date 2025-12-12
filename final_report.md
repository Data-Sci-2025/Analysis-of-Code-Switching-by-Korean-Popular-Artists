
## Introduction

Seventeen is a boy group that holds the current record for best-selling
album from a Korean artist with their 2023 album *FML*. They have
released music since releasing FML and have a long list of frequent
(annual) releases since their 2015 debut a decade ago. They are
self-producing artists, involved in music production, choreographing,
and songwriting.

The Korean music industry has grown and is amassing global attention
like never before. The sound of popular Korean music has changed due to
this global audience, but the language choice of lyrics has also notably
shifted in recent years to include more and more English.

This study aims to serve as a case study of bilingual language use by
popular Korean artists through the Korean pop boy group, Seventeen. By
analyzing Seventeen’s Korean and English lyrics at key junctures in
their career, this research assumes the sociolinguistic theories of
Communication Accommodation (Howard Giles) and Audience Design (Allan
Bell) will provide an understanding of their reasoning behind any
language trends. These core theories support the idea that speakers
shift their speech to accommodate who they are addressing or who might
be hearing/overhearing them and are extended to the communication medium
of music lyrics for this case study.

## Research Questions

I pose three research questions for this study:

1.  Does Seventeen adapt their language choice in later releases?

- Later releases generally receive higher praise and reach higher on the
  charts. I would assume that any change in the language makeup of their
  languages would follow this chart success, meaning that later releases
  have a different language distribution of English and Korean.

2.  Is popularity related to language use?

- Because Seventeen experiences diverse, global success with their
  best-selling, 2023 album, I would expect that their use of English
  increases over time to accommodate for a more global and diverse
  audience of listeners. Following the line of thinking presented in
  previous research on style-shifting and code-switching, I predict that
  Seventeen switches much of their lyrics to English over time as their
  popularity increases.

3.  Does the type of track have any correlation to the language of the
    lyrics?

- I predict that title tracks would include more English than Korean.
  The assumption behind this hypothesis is that title tracks are
  generally made to go viral. Title tracks receive the most
  advertisement and are always accompanied by a music video and a catchy
  dance. If Seventeen (or their company) see that they are gaining
  popularity with an English-speaking demographic, I would find it
  plausible that they include more English in their next ‘centerpiece’
  of a song.

## Data Collection & Results

Lyrics and metadata was collected from a fan-made website called
[colorcodedlyrics.com](https://colorcodedlyrics.com/2015/10/01/seventeen-sebeuntin-lyrics-index/).
The lyrics were recorded in their original (not translated or romanized)
format in individual csv files, which were read in R. Each line of the
songs were saved as their own row, with the spaces between stanzas of
the song preserved as N/As. No metadata was saved inside the files but
rather in the file names.

After tidying the data into its own neat dataframe, functions from the R
package, tidytext, were used to pivot the dataframe to be longer,
assigning each word its own row. In this form the words could be divided
by language. A language column was created using the mutate() function
to save information about which language each individual word token was
written in.

With the lyrics parsed and the language use detected, I could move on to
considering the data as a whole. The language breakdown of the lyrics
altogether lean majority Korean:

**Figure 1**  
![](images/Overall%20Language%20Use.png)

However, it is more important to view the lyrics based off of **when**
they were released. One of the goals of this research was to investigate
whether language use changes over time and/or as their popularity rises.
Both a total count view and a percentage view is provided so that the
language variation within and across each album.

**Figure 2**  
![](images/Language%20Use%20for%20Each%20Album%20Year.png)

**Figure 3**  
![](images/Language%20Comparison%20By%20Album%20Year.png)

Some nuance is lost in this zoomed out view, so I also sorted the
language use by song within each album. Then, I viewed the language use
particularly of the “title” tracks of each album. Figures 4 through 7
show the language percentages of each track in each album.

**Figure 4**  
![](images/Language%20Use%20for%20Debut.png)

**Figure 5**  
![](images/Language%20Use%20for%20Mid-Career.png)

**Figure 6**  
![](images/Language%20Use%20for%20Best-selling.png)

**Figure 7**  
![](images/Language%20Use%20for%20Latest.png)

A title track refers to the song that is mainly promoted from an album.
This title track would have a music video, advertisements leading up to
the album’s release focusing on the track, and would be the song that is
performed on weekly or year-end music shows. Functionally, a title track
is treated differently by fans and artists alike, acting as the
centerpiece to that album’s concept, message, and (in most cases) the
public, ‘non-fan’ image.

**Figure 8**
![](images/Language%20Use%20by%20Nontitle%20vs.%20Title%20Tracks.png)

Across all tracks in the data, title tracks have more English lyrics
than Korean lyrics. However, it is important to consider the content of
these mass totals to ensure a single track or high-frequency token is
skewing the results.

An glance at the English lyrics of the title tracks shows an obvious
higher frequency for words that are in the chorus. The title track from
2020, for example, has a chorus that consists of almost completely
English lyrics, but most of the chorus is just the phrase ‘left and
right’ repeated nine times. Furthermore, this chorus is repeated
multiple times, instantly inflating the use of English in total.

If we view the language distribution of all of the songs at once, we can
see that the non-title tracks are a mixed bag as well. Figure 9 reveals
that many non-title tracks include no Korean, while others include more
English than the title tracks. For example, the song “Together” from
Seventeen’s 2020 album is nearly fully in Korean, but in this same album
we see a non-title track, “Water”, that includes more English than the
title track, “Super”.

**Figure 9**  
![](images/Language%20Use%20by%20Song.png)

While the track-type comparison appears to be unfruitful, a deep look
into the lyric breakdown of the title tracks by themselves provide other
insights on the trend of the language choice. Figures 10 - 13 visualize
the distribution of the English tokens in the lyrics of each title track
of the four albums.

**Figure 10**  
![](images/English%20for%202015%20Title.png)

**Figure 11**  
![](images/English%20for%202020%20Title.png)

**Figure 12**  
![](images/English%20for%202023%20Title.png)

**Figure 13**  
![](images/English%20for%202024%20Title.png)

These graphs when compared side by side suggest that there is a change
in word type over time. Looking at Figure 13, we can see that there is
more variety among the English tokens in the latest title track than
what is observed in the debut title track (Figure 10).

This first glance poses another question toward the general inquiry of
our study: Do the later releases include more complex English structures
than their early counterparts?

This is a trend that can be confirmed by looking closer at English
**function words**. Function words signal the structural relationships
that words have to one another and are generally quite lexically
ambiguous. Examples of English function words would include articles
‘the’ and ‘a’, as well as prepositions, pronouns, conjunctions, and
helping verbs.

Comparing the data to a 200+ word list of common English function words
and dividing the data into two general word types (‘function words’ and
‘content/other words’) does in fact reveal an upward trend in
function-word frequency as time goes on. This increase can be seen in
Figure 14.

**Figure 14**  
![](images/Word%20Type%20by%20Album%20Year.png)

Figure 15 also shows the same upward trend, this time including a rough
depiction of which function words appear in each album. The purpose of
this graph is not to show the exact number of tokens, but the overall
ever-increasing complexity in the distribution of function words from
debut to latest songs.

**Figure 15**  
![](images/English%20Function%20Words%20by%20Album%20Year.png)

**A Note on Interjections**  
Interjections would also be classed as function words since they ‘fill’
pauses and express feeling or reaction in an utterance. However,
interjections in the data were not included in the list of function
words but were left as part of the “Content/Other” category. There are a
few lines of thinking behind this decision. Firstly, these interjections
are not always included in the data in Latin script but in Hangul. This
is true even when the title of the song includes the interjections in
English (i.e. the song “Ah Yeah” includes ‘ah’ and ‘yeah’ only in Hangul
in the lyrics). Secondly, the opposite is frequently also true. There
are non-English words that are written in Latin script. Scats and
‘whoops’ such as “darimdarimda” or “yuh” are labeled as English in the
data because the translators of the songs transcribed them using the
Latin alphabet. It appears that these interjections are some third
option, words serving an overlapping function in both languages. With
these reasons in mind, they were not coded as function words for this
data set.

\##Conclusion

After conducting all of the above analysis, several conclusions can be
made about Seventeen’s discography:

1.  **There is more English in songs later in their career than
    earlier/mid-career.**

- The total number of individual words in the songs may still majorly
  favor Korean, a comparison of the language usage across albums showed
  that later albums increase in English lyrics distribution, especially
  after their best-selling album in 2023 (see Figure 3).

2.  **There are more unique and complex English lyrics in later
    releases.**

- An analysis of what type of English words are present in each title
  track and overall track list revealed that Seventeen had much simpler
  English words and structure in their debut release than their latest
  tracks. An overview revealed this upward trend roughly mirrored the
  increase in English we saw in the language distribution of the lyrics.

3.  **There is only slightly more English in title vs non-title
    tracks.**

- The third research question of this study aimed to investigate whether
  there is a difference in language use between title and non-title
  tracks in general. Figure 8 shows a slight favor towards English, but
  a closer look at the individual songs showed a more untidy
  distribution.

## Research Limitations & Future Directions

There are a few limitations to this study that if addressed would
improve it considerably. Firstly, the data pool is admittedly small.
With only four extended plays (EPs), we only get a murky view of
Seventeen’s decade-long discography. While these albums were not chosen
thoughtfully, it still would solidify any conclusions drawn to have a
larger data pool. Widening the pool to include all of their EPs would
make this research much more valuable and statistically sound.

Linguistically, there are many directions that I could have taken to
observe the group’s language use that were not taken due because of time
constraints. For example, there may be a pattern of word type for the
English Seventeen uses in the choruses of their songs versus the rap
sections or verses. Investigating whether this is realized in the data
would require a lot of hand-coding and analysis that is not the main
focus of this project, but would be a natural next step.

For future directions, this research could easily be extended in the
ways I outlined above or by repeating the same methods of analysis for
other popular Korean artists. A more robust future approach would be to
look at several other similar “veteran artists” and the language
breakdown of their discography. A several-artist approach could also be
informative. This could look like conducting a yearly comparison of
their collective language usage a decade ago versus now when several
Korean artists have chart-topping songs in the United States and other
primarily English-speaking countries.

The assumption underlying the conclusions of this research and the
suggested future directions is that international, non-Korean-speaking
fans desire, enjoy, or prefer for the Korean musicians to release songs
with more English lyrics. However, this is a sentiment that does not
necessarily have the evidence to support it– Do English songs released
by Korean artists perform better in the market? Do the English releases
bring in new fans? Do newer artists who release music with
English-focused lyrics perform successfully outside of the South Korean
music market? These questions challenge the assumption of this study and
the artists (or producers) that continue to leave their native language
behind for the ever-expanding *lingua franca* that is the English
language.

## References

Billboard. (2025). “Seventeen: Biography, Music & News. Billboard”.
https://www.billboard.com/artist/seventeen/chart-history/hsi/

ColorCodedLyrics.com. (2025). “SEVENTEEN (세븐틴) Profile & Lyrics
Index”
https://colorcodedlyrics.com/2015/10/01/seventeen-sebeuntin-lyrics-index/

Meyerhoff, M. (2019). Variation and style. In *Introducing
Sociolinguistics* (pp. 31–57). essay, Routledge/Taylor and Francis
Group.

Wikipedia. “Category: English-language South Korean songs”
https://en.wikipedia.org/wiki/Category:English-language_South_Korean_songs

### Acknowledgement of AI Use

Chat-GPT was used to as a reference resource for a few things during the
research process. Below are links to the relevant chats:

- Hangul Unicode:
  https://chatgpt.com/c/691f32f7-b0c4-8327-970b-9282d4c5210f (November
  2025)

This chat session informed me that the first and last Unicode for Hangul
are “가” and “힣”. This knowledge was used to help me properly detect
the use of Hangul characters in my data and divide the Korean lyrics
from the English lyrics.

- **mutate()** template and functionality:
  https://chatgpt.com/c/691f36c1-56d0-8332-911d-6f609f8f34e9 (November
  2025)

This session was used to compare my mutate() code for creating columns
for the metadata of the csv files and try to assess what I had forgotten
to include. Chat GPT was only referred to after looking first to the
information included in Rstudio using “?mutate()”, in-class notes, and a
general Google search.

- Reading From a Subfolder in R:
  https://chatgpt.com/c/693af40d-666c-8326-933f-70a027a5c3fc (December
  11, 2025)

Creating a folder and placing my csv files into it broke my code, and
after many failed iterations of the changing my working directory and
**read_csv** pipelines, I asked ChatGPT for a general template of how to
read multiple csv files from a subfolder in my directory. I used its
suggestions about creating an object to refer to the subfolder and then
using that object in my **list.files()** code.

- Common Function Words in English:
  https://chatgpt.com/c/693b1e57-a468-8333-9597-08e1774b7ccc (December
  11, 2025)

I wanted a large list of common function words in English to act as my
‘stopwords’ that I could compare my data to and sort it into function
versus content words. ChatGPT gave me a list of 200+ function words that
I included as a vector in R. While the faster option, it gave me more
than I specified and was likely not the best option for this list
generation.

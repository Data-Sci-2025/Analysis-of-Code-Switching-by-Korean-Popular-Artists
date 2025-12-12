---
format: gfm
---

## Introduction

## Previous Research 

## Research Questions

## Data Methods & Collection 










A title track refers to the song that is mainly promoted from an album. This title track would have a music video, advertisements leading up to the album's release focusing on the track, and would be the song that is performed on weekly or year-end music shows. Functionally, a title track is treated differently by fans and artists alike, acting as the centerpiece to that album's concept, message, and (in most cases) the public, 'non-fan' image. 





An overlook at the English lyrics of the title tracks shows an obvious higher frequency for words that are in the chorus. This is sensical-- the chorus in each song is repeated multiple times, instantly inflating the use of English in each song. However, these graphs when compared side by side suggest that there is possibly a change in word type over time. 




 Function words signal the structural relationships that words have to one another and are generally quite lexically ambiguous. Examples of English function words would include articles 'the' and 'a', as well as prepositions, pronouns, conjunctions, and helping verbs. 
 
 
 Interjections would also be classed as function words since they 'fill' pauses and express feeling or reaction in an utterance. Interjections in the data were not included in the list of function words above but were left as part of the "Content/Other" category. There are a few lines of thinking behind this decision. Firstly, these interjections are not always included in the data in Latin script but in Hangul. This is true even when the title includes the interjections in English (i.e. the song "Ah Yeah" includes its name only in Hangul in the lyrics). Secondly, the opposite is frequently also true. There are non-English words that are written in Latin script. Scats and 'whoops' such as "darimdarimda" or "yuh" are sorted by the code as English because the translators of the songs transcribed them using the Latin alphabet. It appears that these interjections are some third option, words serving an overlapping function in both languages. With these reasons in mind, they were not coded as function words for this data set.  
 
 
 
## Drawing Conclusions


There is more English in songs later in career than earlier/mid-career.
There is more English in songs after best-selling album, as well as collaborations with Western producers.
More unique English words (and more content/function words) in later releases
Only slightly more English in title vs non-title tracks.



## Research Limitations & Future Directions

There are a few limitations to this study that if addressed would improve it considerably. Firstly, the data pool is admittedly small. With only four extended plays (EPs), we only get a murky view of Seventeen's decade-long discography. While these albums were not chosen thoughtfully, it still would solidify any conclusions drawn to have a larger data pool. Widening the pool to include all of their EPs would make this research much more valuable and statistically sound. 

Linguistically, there are many directions that I could have taken to observe the group's language use that were not taken due because of time constraints. For example, there may be a pattern of word type for the English Seventeen uses in the choruses of their songs versus the rap sections or verses. Investigating whether this is realized in the data would require a lot of hand-coding and analysis that is not the main focus of this project, but would be a natural next step.

For future directions, this research could easily be extended in the ways I outlined above or by repeating the same methods of analysis for other popular Korean artists. A more robust future approach would be to look at several other similar “veteran artists” and the language breakdown of their discography. A several-artist approach could also be informative. This could look like conducting a yearly comparison of their collective language usage a decade ago versus now when several Korean artists have chart-topping songs in the United States and other primarily English-speaking countries.

The assumption underlying the conclusions of this research and the suggested future directions is that international, non-Korean-speaking fans desire, enjoy, or prefer for the Korean musicians to release songs with more English lyrics. However, this is a sentiment that does not necessarily have the evidence to support it-- Do English songs released by Korean artists perform better in the market? Do the English releases bring in new fans? Do newer artists who release music with English-focused lyrics perform successfully outside of the South Korean music market? These questions challenge the assumption of this study and the artists (or producers) that continue to leave their native language behind for the ever-expanding *lingua franca* that is the English language.

## References


ColorCodedLyrics.com.“SEVENTEEN (세븐틴) Profile & Lyrics Index” https://colorcodedlyrics.com/2015/10/01/seventeen-sebeuntin-lyrics-index/ 

Meyerhoff, M. (2019). Variation and style. In *Introducing Sociolinguistics* (pp. 31–57). essay, Routledge/Taylor and Francis Group. 

Wikipedia. “Category: English-language South Korean songs” https://en.wikipedia.org/wiki/Category:English-language_South_Korean_songs 



### Acknowledgement of AI Use

Chat-GPT was used to as a reference resource for a few things during the research process. Below are links to the relevant chats: 

- Hangul Unicode: https://chatgpt.com/c/691f32f7-b0c4-8327-970b-9282d4c5210f 
(November 2025)

This chat session informed me that the first and last Unicode for Hangul are "가" and "힣". This knowledge was used to help me properly detect the use of Hangul characters in my data and divide the Korean lyrics from the English lyrics.

- **mutate()** template and functionality: https://chatgpt.com/c/691f36c1-56d0-8332-911d-6f609f8f34e9 
(November 2025)

This session was used to compare my mutate() code for creating columns for the metadata of the csv files and try to assess what I had forgotten to include. Chat GPT was only referred to after looking first to the information included in Rstudio using "?mutate()", in-class notes, and a general Google search. 

- Reading From a Subfolder in R: https://chatgpt.com/c/693af40d-666c-8326-933f-70a027a5c3fc 
(December 11, 2025)

Creating a folder and placing my csv files into it broke my code, and after many failed iterations of the changing my working directory and **read_csv** pipelines, I asked ChatGPT for a general template of how to read multiple csv  files from a subfolder in my directory. I used its suggestions about creating an object to refer to the subfolder and then using that object in my **list.files()** code.

- Common Function Words in English: https://chatgpt.com/c/693b1e57-a468-8333-9597-08e1774b7ccc 
(December 11, 2025)

I wanted a large list of common function words in English to act as my 'stopwords' that I could compare my data to and sort it into function versus content words. ChatGPT gave me a list of 200+ function words that I included as a vector in R. While the faster option, it gave me more than I specified and was likely not the best option for this list generation.



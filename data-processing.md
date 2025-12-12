
## Table of Contents

- [Reading in the Data](#reading-in-the-data)
- [Tidying the Data](#tidying-the-data)
- [Language Detection](#language-detection)
- [Visualizing and Analyzing the
  Data](#visualizing-and-analyzing-the-data)
- [Zooming in on Track Type](#zooming-in-on-track-type)
- [English Highlights](#english-highlights)

## Reading in the Data

Below shows the code I used to read in the data, where each song is its
own csv file. I then created columns for the metadata associated with
each song.

``` r
#reading in packages I will need
library(tidyverse)
```

    ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ✔ ggplot2   3.5.2     ✔ tibble    3.3.0
    ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ✔ purrr     1.1.0     
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()
    ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(dplyr)
library(stringr)
library(tidytext)

# Path to the subfolder
data_subfolder <- "Seventeen_Lyrics"

# Get full file paths of all CSVs in the subfolder
files <- list.files(path = data_subfolder, pattern = "\\.csv$", full.names = TRUE)
firstfiles <- read_csv(files,id = "file", na = c("", "na", "n/a", "N/A", "NA", "Na"))
```

    Rows: 1582 Columns: 2
    ── Column specification ────────────────────────────────────────────────────────
    Delimiter: ","
    chr (1): Lyrics

    ℹ Use `spec()` to retrieve the full column specification for this data.
    ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
# Read all CSVs into a list of data frames
# <- read_csv(id = "file", na = c("", "na", "n/a", "N/A", "NA", "Na"))


#firstfiles$file = as.character(file)
firstfiles$track_type = str_extract(firstfiles$file, "Title|Nontitle")
firstfiles$album_year = str_extract(firstfiles$file, "15|20|23|24")

 
#separating out the song names using str_detect and mutate functions
lyrics = firstfiles |>
  mutate(
    file = as.character(file),
  song_title = case_when(
    str_detect(file, "Nontitle_Ah_Yeah_15.csv") ~ "Ah Yeah",
    str_detect(file, "Nontitle_April_shower_23.csv") ~ "April Shower",
    str_detect(file, "Nontitle_Candy_24.csv") ~ "Candy",
    str_detect(file, "Nontitle_Dust_23.csv") ~ "Dust",
    str_detect(file, "Nontitle_Eyes_On_You_24.csv") ~ "Eyes On You",
    str_detect(file, "Nontitle_F_ck_My_Life_23.csv") ~ "F_ck My Life",
    str_detect(file, "Nontitle_Fearless_20.csv") ~ "Fearless",
    str_detect(file, "Nontitle_Fire_23.csv") ~ "Fire",
    str_detect(file, "Nontitle_I_Dont_Understand_But_I_Luv_U_23.csv") ~ "I Don't Understand But I Luv U",
    str_detect(file, "Nontitle_I_Wish_20.csv") ~ "I Wish",
    str_detect(file, "Nontitle_Jam_Jam_15.csv") ~ "Jam Jam",
    str_detect(file, "Nontitle_Kidult_20.csv") ~ "Kidult",
    str_detect(file, "Nontitle_My_My_20.csv") ~ "My My",
    str_detect(file, "Nontitle_Rain_24.csv") ~ "Rain",
    str_detect(file, "Nontitle_Shining_Diamond_15.csv") ~ "Shining Diamond",
    str_detect(file, "Nontitle_Together_20.csv") ~ "Together",
    str_detect(file, "Nontitle_Twenty_15.csv") ~ "Twenty",
    str_detect(file, "Nontitle_Water_24.csv") ~ "Water",
    str_detect(file, "Title_Adore_U_15.csv") ~ "Adore U",
    str_detect(file, "Title_Left_and_Right_20.csv") ~ "Left and Right",
    str_detect(file, "Title_Love_Money_Fame_24.csv") ~ "Love Money Fame",
    str_detect(file, "Title_One_to_Thirteen_24.csv") ~ "One to Thirteen",
    str_detect(file, "Title_Super_23.csv") ~ "Super"),
  #reformatting the year of each album to be written out fully
  album_year = case_when(
    str_detect(album_year, "24") ~ "2024",
    str_detect(album_year, "23") ~ "2023",
    str_detect(album_year, "20") ~ "2020",
    str_detect(album_year, "15") ~ "2015")
  ) ->> lyrics

colnames(lyrics) <- tolower(colnames(lyrics))
lyrics
```

    # A tibble: 1,582 × 5
       file                                  lyrics track_type album_year song_title
       <chr>                                 <chr>  <chr>      <chr>      <chr>     
     1 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 아 예 아… Nontitle   2015       Ah Yeah   
     2 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… Yo $.… Nontitle   2015       Ah Yeah   
     3 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 등장과 동… Nontitle   2015       Ah Yeah   
     4 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 침 흘리며… Nontitle   2015       Ah Yeah   
     5 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… WOAH … Nontitle   2015       Ah Yeah   
     6 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 애들이 알… Nontitle   2015       Ah Yeah   
     7 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 못 뜬 이… Nontitle   2015       Ah Yeah   
     8 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 맞출 생각… Nontitle   2015       Ah Yeah   
     9 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 니 식견에… Nontitle   2015       Ah Yeah   
    10 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 막 귀들 … Nontitle   2015       Ah Yeah   
    # ℹ 1,572 more rows

## Tidying the Data

After reading in the individual files of each song and creating neat
columns for the metadata related to each song, I end up with a tidy
dataframe called “lyrics”:

``` r
lyrics 
```

    # A tibble: 1,582 × 5
       file                                  lyrics track_type album_year song_title
       <chr>                                 <chr>  <chr>      <chr>      <chr>     
     1 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 아 예 아… Nontitle   2015       Ah Yeah   
     2 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… Yo $.… Nontitle   2015       Ah Yeah   
     3 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 등장과 동… Nontitle   2015       Ah Yeah   
     4 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 침 흘리며… Nontitle   2015       Ah Yeah   
     5 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… WOAH … Nontitle   2015       Ah Yeah   
     6 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 애들이 알… Nontitle   2015       Ah Yeah   
     7 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 못 뜬 이… Nontitle   2015       Ah Yeah   
     8 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 맞출 생각… Nontitle   2015       Ah Yeah   
     9 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 니 식견에… Nontitle   2015       Ah Yeah   
    10 Seventeen_Lyrics/Nontitle_Ah_Yeah_15… 막 귀들 … Nontitle   2015       Ah Yeah   
    # ℹ 1,572 more rows

With this “lyrics” dataframe, I can then pivot the data to be longer,
making each word of the song lyrics its own row:

``` r
#putting each word of the lyrics as its own row and feeding it back into the dataframe
lyrics |> 
  unnest_tokens(word, "lyrics") |> arrange(desc(album_year)) -> lyrics
lyrics
```

    # A tibble: 6,418 × 5
       file                                   track_type album_year song_title word 
       <chr>                                  <chr>      <chr>      <chr>      <chr>
     1 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      우리 
     2 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      사탕 
     3 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      같은 
     4 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      사랑해요…
     5 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      자그만……
     6 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      말   
     7 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      하나에도…
     8 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      기분이……
     9 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      좋아질……
    10 Seventeen_Lyrics/Nontitle_Candy_24.csv Nontitle   2024       Candy      수   
    # ℹ 6,408 more rows

### Language Detection

Now that each word can be evaluated separately, I can detect the
language of the word. Because Korean and English use separate alphabets,
I simply used stringr functions to detect Hangul versus Latin alphabet
use in each word. A new column was created to hold the information on
the language of the words. The mutated “lyrics” dataframe that contains
this new column was renamed to “lyricsdf”.

``` r
#mutating the dataframe to detect language of rows of lyrics and create language column
lyricdf <- lyrics |>
  mutate(
    word   = as.character(word),
  language = case_when(
  str_detect(word, "[가-힣]") ~ "Korean",
  str_detect(word, "[a-zA-z 12345]") ~ "English"
)) ->> lyricsdf
  
lyricsdf
```

    # A tibble: 6,418 × 6
       file                          track_type album_year song_title word  language
       <chr>                         <chr>      <chr>      <chr>      <chr> <chr>   
     1 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      우리  Korean  
     2 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      사탕  Korean  
     3 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      같은  Korean  
     4 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      사랑해요… Korean  
     5 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      자그만…… Korean  
     6 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      말    Korean  
     7 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      하나에도… Korean  
     8 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      기분이…… Korean  
     9 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      좋아질…… Korean  
    10 Seventeen_Lyrics/Nontitle_Ca… Nontitle   2024       Candy      수    Korean  
    # ℹ 6,408 more rows

## Visualizing and Analyzing the Data

### Language Use Overview

With the lyrics parsed and the language use detected, I could move on to
considering the data as a whole.

The language breakdown of the lyrics altogether lean majority Korean:

``` r
#to count the language breakdown of the lyrics overall
lyricsdf |> count(language, sort=TRUE)
```

    # A tibble: 3 × 2
      language     n
      <chr>    <int>
    1 Korean    3621
    2 English   2508
    3 <NA>       289

``` r
#...and visualize it:
ggplot(data=subset(lyricsdf, !is.na(language)), aes(x = language)) +
  geom_bar(fill = "salmon")+ theme_light() + xlab("Language") + ylab("Count") + labs(title = "Overall Language Use")
```

![](images/unnamed-chunk-5-1.png)

### Language Use by Album

However, it is more important to view the lyrics based off of **when**
they were released. One of the goals of this research was to investigate
whether language use changes over time and/or as their popularity rises.
Both a total count view and a percentage view is provided so that the
language variation within and across each album.

``` r
#code meant to count the language breakdown of lyrics by album
table(lyricsdf$album_year, lyricsdf$language)
```

          
           English Korean
      2015     828    980
      2020     494   1031
      2023     476    944
      2024     710    666

``` r
#...and visualize it:
ggplot(data=subset(lyricsdf, !is.na(language)), aes(x = language, fill = album_year, na.rm = FALSE)) +
  geom_bar(position = "dodge") + xlab("Language") + ylab("Lyrics") + labs(fill = "Album Year")  + labs(title = "Language Use for Each Album Year")
```

![](images/unnamed-chunk-6-1.png)

``` r
ggsave("Language Use for Each Album Year.png")
```

    Saving 7 x 5 in image

``` r
ggplot(data=subset(lyricsdf, !is.na(language)), aes(x = album_year, fill = language)) +
  geom_bar(position = "fill") + xlab("Album Year") + ylab("Lyrics") + labs(fill = "Language") + labs(title = "Language Comparison by Album Year")
```

![](images/unnamed-chunk-6-2.png)

### Zooming in on Track Type

``` r
#sorting songs into albums:
filter(lyricsdf, album_year == "2024") ->> byalbum24
filter(lyricsdf, album_year == "2023") ->> byalbum23
filter(lyricsdf, album_year == "2020") ->> byalbum20
filter(lyricsdf, album_year == "2015") ->> byalbum15

#visualizing language use by album and song using objects from above ^: 
ggplot(data=subset(byalbum15, !is.na(language)), aes(y = song_title, fill = language)) +
  geom_bar(position = "fill") + xlab("Lyrics") + ylab("Songs") + labs(title= "Language Use for Debut (2015) Album")
```

![](images/unnamed-chunk-7-1.png)

``` r
ggplot(data=subset(byalbum20, !is.na(language)), aes(y = song_title, fill = language)) +
  geom_bar(position = "fill") + xlab("Lyrics") + ylab("Songs") + labs(title= "Language Use for Mid-Career (2020) Album")
```

![](images/unnamed-chunk-7-2.png)

``` r
ggplot(data=subset(byalbum23, !is.na(language)), aes(y = song_title, fill = language)) +
  geom_bar(position = "fill") + xlab("Lyrics") + ylab("Songs") + labs(title= "Language Use for Best-selling (2023) Album")
```

![](images/unnamed-chunk-7-3.png)

``` r
ggplot(data=subset(byalbum24, !is.na(language)), aes(y = song_title, fill = language)) +
  geom_bar(position = "fill") + xlab("Lyrics") + ylab("Songs") + labs(title= "Language Use for Latest (2024) Album")
```

![](images/unnamed-chunk-7-4.png)

``` r
#filtering so that only the title tracks are included:
filter(lyricsdf, song_title == "Adore U") ->> debuttitle
filter(lyricsdf, song_title == "Left and Right") ->> midtitle
filter(lyricsdf, song_title == "Super") ->> bestitle
filter(lyricsdf, song_title == "Love Money Fame") ->> latesttitle


#visualizing the language breakdown of each title track:
ggplot(data=subset(debuttitle, !is.na(language)), aes(x = language, fill = language)) +
  geom_bar(position = "dodge") + xlab("Language of Lyrics") + ylab("Count") + labs(title= "Language Breakdown for 'Adore U' (2015)")
```

![](images/unnamed-chunk-7-5.png)

``` r
ggplot(data=subset(midtitle, !is.na(language)), aes(x = language, fill = language)) +
  geom_bar(position = "dodge") + xlab("Language of Lyrics") + ylab("Count") + labs(title= "Language Breakdown for 'Left and Right' (2020)")
```

![](images/unnamed-chunk-7-6.png)

``` r
ggplot(data=subset(bestitle, !is.na(language)), aes(x = language, fill = language)) +
  geom_bar(position = "dodge") + xlab("Language of Lyrics") + ylab("Count") + labs(title= "Language Breakdown for 'Super' (2023)")
```

![](images/unnamed-chunk-7-7.png)

``` r
ggplot(data=subset(latesttitle, !is.na(language)), aes(x = language, fill = language)) +
  geom_bar(position = "dodge") + xlab("Language of Lyrics") + ylab("Count") + labs(title= "Language Breakdown for 'Love, Money, Fame' (2024)")
```

![](images/unnamed-chunk-7-8.png)

### English Highlights

``` r
#taking a closer look at the English lyrics in each title track: 
filter(debuttitle, language == "English") ->> adoreu
filter(midtitle, language == "English") ->> leftright
filter(bestitle, language == "English") ->> super
filter(latesttitle, language == "English") ->> lovemoneyfame


#visualization for English lyrics in 2024 title track:
ggplot(data=subset(lovemoneyfame, !is.na(language)), aes(y = word, fill = word)) +
  geom_bar(position = "dodge") + xlab("Count") + ylab("English Words") + labs(title= "English Lyrics for 'Love, Money, Fame'") + theme(axis.title.y=element_blank(),
         axis.text.y=element_blank(),
        axis.ticks.y=element_blank())
```

![](images/unnamed-chunk-8-1.png)

``` r
#visualization for English lyrics in 2023 title track: 
ggplot(data=subset(super, !is.na(language)), aes(y = word, fill = word)) +
  geom_bar(position = "dodge") + xlab("Count") + ylab("English Words") + labs(title= "English Lyrics for 'Super'") + theme(axis.title.y=element_blank(),
         axis.text.y=element_blank(),
        axis.ticks.y=element_blank())
```

![](images/unnamed-chunk-8-2.png)

``` r
#visualization for English lyrics in 2020 title track: 
ggplot(data=subset(leftright, !is.na(language)), aes(y = word, fill = word)) +
  geom_bar(position = "dodge") + xlab("Count") + ylab("English Words") + labs(title= "English Lyrics for 'Left and Right'") + theme(axis.title.y=element_blank(),
         axis.text.y=element_blank(),
        axis.ticks.y=element_blank())
```

![](images/unnamed-chunk-8-3.png)

``` r
#visualization for English lyrics in 2015 title track: 
ggplot(data=subset(adoreu, !is.na(language)), aes(y = word, fill = word)) +
  geom_bar(position = "dodge") + xlab("Count") + ylab("English Words") + labs(title= "English Lyrics for 'Adore U'") + theme(axis.title.y=element_blank(),
         axis.text.y=element_blank(),
        axis.ticks.y=element_blank())
```

![](images/unnamed-chunk-8-4.png)

Do the later releases include more complex English structures than their
early counterparts? This is a trend that can be confirmed by looking
closer at English **function words**.

``` r
#long list of common function words in English
stopwords <- c(
  "a","about","above","across","after","again","against","all","almost",
  "along","already","also","although","always","am","among","an","and",
  "another","any","anybody","anyone","anything","anywhere","are","around",
  "as","at","away","back","be","became","because","become","becomes",
  "been","before","being","below","between","both","but","by","can",
  "cannot","could","did","do","does","doing","done","down","during",
  "each","either","else","enough","even","ever","every","everybody",
  "everyone","everything","everywhere","few","fewer","for","from","further",
  "had","has","have","having","he","her","here","hers","herself","him",
  "himself","his","how","however","i","I", "if","in","inside","instead","into",
  "is","it","its","itself","just","least","less","let","like","likely",
  "little","long","may","me","might","more","most","mostly","much","must",
  "my","myself","near","neither","never","no","nobody","none","nor","not",
  "nothing","now","nowhere","of","off","often","on","once","one","only",
  "onto","or","other","others","otherwise","our","ours","ourselves","out",
  "outside","over","own","per","perhaps","please","quite","rather","really",
  "said","same","seem","seemed","seeming","seems","several","shall","she",
  "should","since","so","some","somebody","someone","something","sometimes",
  "somewhere","soon","still","such","than","that","the","their","theirs",
  "them","themselves","then","there","therefore","these","they","this",
  "those","though","through","throughout","thus","to","together","too",
  "toward","towards","under","until","up","upon","us","usually","very",
  "via","was","we","well","were","what","whatever","when","whenever",
  "where","wherever","whether","which","while","whilst","who","whoever",
  "whom","whomever","whose","why","will","with","within","without","would",
  "yes","yet","you","your","yours","yourself","yourselves"
)

#sorting the lyrics into function or content/other categories using the list above
lyric_wordtype <- lyricdf |>
  mutate(
    cont_func = if_else(
      word %in% stopwords,
      "Function",
      "Content/Other" ))
lyric_wordtype
```

    # A tibble: 6,418 × 7
       file                track_type album_year song_title word  language cont_func
       <chr>               <chr>      <chr>      <chr>      <chr> <chr>    <chr>    
     1 Seventeen_Lyrics/N… Nontitle   2024       Candy      우리  Korean   Content/…
     2 Seventeen_Lyrics/N… Nontitle   2024       Candy      사탕  Korean   Content/…
     3 Seventeen_Lyrics/N… Nontitle   2024       Candy      같은  Korean   Content/…
     4 Seventeen_Lyrics/N… Nontitle   2024       Candy      사랑해요… Korean   Content/…
     5 Seventeen_Lyrics/N… Nontitle   2024       Candy      자그만…… Korean   Content/…
     6 Seventeen_Lyrics/N… Nontitle   2024       Candy      말    Korean   Content/…
     7 Seventeen_Lyrics/N… Nontitle   2024       Candy      하나에도… Korean   Content/…
     8 Seventeen_Lyrics/N… Nontitle   2024       Candy      기분이…… Korean   Content/…
     9 Seventeen_Lyrics/N… Nontitle   2024       Candy      좋아질…… Korean   Content/…
    10 Seventeen_Lyrics/N… Nontitle   2024       Candy      수    Korean   Content/…
    # ℹ 6,408 more rows

``` r
#subset that only hold lyrics that are function words in English
function_subset <- filter(lyric_wordtype, cont_func == "Function")
function_subset
```

    # A tibble: 880 × 7
       file                track_type album_year song_title word  language cont_func
       <chr>               <chr>      <chr>      <chr>      <chr> <chr>    <chr>    
     1 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… on    English  Function 
     2 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… you   English  Function 
     3 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… on    English  Function 
     4 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… me    English  Function 
     5 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… on    English  Function 
     6 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… you   English  Function 
     7 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… on    English  Function 
     8 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… me    English  Function 
     9 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… so    English  Function 
    10 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… under English  Function 
    # ℹ 870 more rows

``` r
#counting the lyrics that match the function word list:
function_freq <- function_subset %>%
  count(song_title, cont_func, sort = TRUE)
function_freq
```

    # A tibble: 19 × 3
       song_title                     cont_func     n
       <chr>                          <chr>     <int>
     1 Shining Diamond                Function     89
     2 Ah Yeah                        Function     88
     3 One to Thirteen                Function     82
     4 Love Money Fame                Function     75
     5 Left and Right                 Function     73
     6 Eyes On You                    Function     70
     7 April Shower                   Function     56
     8 Super                          Function     55
     9 I Don't Understand But I Luv U Function     48
    10 Twenty                         Function     48
    11 Fire                           Function     43
    12 Fearless                       Function     33
    13 Water                          Function     27
    14 My My                          Function     26
    15 Jam Jam                        Function     21
    16 Rain                           Function     20
    17 Kidult                         Function     12
    18 F_ck My Life                   Function      8
    19 Adore U                        Function      6

``` r
#checking that there aren't any function words labeled as content words:
content_subset <- filter(lyric_wordtype, language == "English", cont_func == "Content/Other")
content_subset
```

    # A tibble: 1,628 × 7
       file                track_type album_year song_title word  language cont_func
       <chr>               <chr>      <chr>      <chr>      <chr> <chr>    <chr>    
     1 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… eyes  English  Content/…
     2 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… eyes  English  Content/…
     3 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… eyes  English  Content/…
     4 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… eyes  English  Content/…
     5 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… sweet English  Content/…
     6 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… moon… English  Content/…
     7 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… matt… English  Content/…
     8 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… prom… English  Content/…
     9 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… bpm   English  Content/…
    10 Seventeen_Lyrics/N… Nontitle   2024       Eyes On Y… heart English  Content/…
    # ℹ 1,618 more rows

Interjections would also be classed as function words since they ‘fill’
pauses and express feeling or reaction in an utterance. Interjections in
the data were not included in the list of function words above but were
left as part of the “Content/Other” category.

``` r
ggplot(data=subset(lyric_wordtype, !is.na(language)), aes(x = album_year, fill = cont_func)) +
  geom_bar(position = "fill") + xlab("Album Year") + ylab("Word Type") + labs(fill = "Language") + labs(title = "Word Type by Album Year")
```

![](images/unnamed-chunk-10-1.png)

``` r
ggplot(data=subset(function_subset), aes(x = album_year, fill = cont_func)) +
  geom_bar(position = "dodge") + xlab("Count") + ylab("Function Words") + labs(title= "English Function Words by Year")
```

![](images/unnamed-chunk-11-1.png)

``` r
#A rough visualization of what function words are in each album
ggplot(data=subset(function_subset), aes(x = album_year, fill = word)) +
  geom_bar(position = "dodge") + xlab("Count") + ylab("Function Wordss") + labs(title= "English Function Words by Year") + theme(axis.title.y=element_blank(),
         axis.text.y=element_blank(),
        axis.ticks.y=element_blank())
```

![](images/unnamed-chunk-11-2.png)

``` r
#Session Info
sessionInfo()
```

    R version 4.5.1 (2025-06-13 ucrt)
    Platform: x86_64-w64-mingw32/x64
    Running under: Windows 10 x64 (build 19045)

    Matrix products: default
      LAPACK version 3.12.1

    locale:
    [1] LC_COLLATE=English_United States.utf8 
    [2] LC_CTYPE=English_United States.utf8   
    [3] LC_MONETARY=English_United States.utf8
    [4] LC_NUMERIC=C                          
    [5] LC_TIME=English_United States.utf8    

    time zone: America/New_York
    tzcode source: internal

    attached base packages:
    [1] stats     graphics  grDevices utils     datasets  methods   base     

    other attached packages:
     [1] tidytext_0.4.3  lubridate_1.9.4 forcats_1.0.0   stringr_1.5.1  
     [5] dplyr_1.1.4     purrr_1.1.0     readr_2.1.5     tidyr_1.3.1    
     [9] tibble_3.3.0    ggplot2_3.5.2   tidyverse_2.0.0

    loaded via a namespace (and not attached):
     [1] janeaustenr_1.0.0  utf8_1.2.6         generics_0.1.4     stringi_1.8.7     
     [5] lattice_0.22-7     hms_1.1.3          digest_0.6.37      magrittr_2.0.3    
     [9] evaluate_1.0.5     grid_4.5.1         timechange_0.3.0   RColorBrewer_1.1-3
    [13] fastmap_1.2.0      jsonlite_2.0.0     Matrix_1.7-3       scales_1.4.0      
    [17] textshaping_1.0.1  cli_3.6.5          rlang_1.1.6        crayon_1.5.3      
    [21] tokenizers_0.3.0   bit64_4.6.0-1      withr_3.0.2        yaml_2.3.10       
    [25] tools_4.5.1        parallel_4.5.1     tzdb_0.5.0         vctrs_0.6.5       
    [29] R6_2.6.1           lifecycle_1.0.4    bit_4.6.0          vroom_1.6.5       
    [33] ragg_1.4.0         pkgconfig_2.0.3    pillar_1.11.0      gtable_0.3.6      
    [37] glue_1.8.0         Rcpp_1.1.0         systemfonts_1.2.3  xfun_0.52         
    [41] tidyselect_1.2.1   rstudioapi_0.17.1  knitr_1.50         farver_2.1.2      
    [45] htmltools_0.5.8.1  SnowballC_0.7.1    labeling_0.4.3     rmarkdown_2.30    
    [49] compiler_4.5.1    

---
title: Spanish Stopwords for tidytext package
author: jvera
date: '2017-10-16'
slug: spanish-stopwords-for-tidytext-package
categories:
  - packages
  - tricks
tags:
  - text mining
---

As a clever friend of mine says, the main programming language, is not Java or Python but English.

So, when you're searching for help, you'll be much successful if searching in english. The main docs are in english, and if the topic is a bit obscure or not mainstream, you'll be lucky if there's some documents even in english. Searching for spanish documentation can lead you to bad translation for the best, or none at all for the worst.

This issue is best known for all of us that had the opportunity of doing some text mining. As you surely know, for a proper text analytics, text must be stripped of "non informative" tokens. I refer to words like (in spanish): de, la, que.

So, you started your Rstudio project, loaded tidytext library, and then, when reaching the point where you have a line like this:

```
df_text <- my_spanish_text %>% 
           unnest_tokens(word, text_line) %>%
           anti_join(stop_words)

```

Nothing happened. You won't notice that no token has been stripped. The reason is there's no spanish lexicon in tidytext package.

One of the solutions I've tested myself is to add your own stopwords. Instead of adding it all by hand you can get lists from some other sites like:

https://github.com/stopwords-iso/stopwords-es

http://countwordsfree.com/stopwords/spanish

Or you can add stopwords *borrowing* them from other text mining packages as **quanteda** or **tm**. Install those mentioned packages for the next chunk of code to properly work.

```
custom_stop_words <- bind_rows(stop_words,
                               data_frame(word = tm::stopwords("spanish"),
                                          lexicon = "custom"))
                                          
custom_stop_words <- bind_rows(stop_words,
                               data_frame(word = quanteda::data_char_stopwords$spanish,
                                          lexicon = "custom"))
df_text <- df_text %>% 
    unnest_tokens(word, text) %>%
    anti_join(custom_stop_words) %>%
    count(word, sort = TRUE)

```


et voilà!  All spanish stopwords are out of the corpus and you can follow the procedures for text mining.

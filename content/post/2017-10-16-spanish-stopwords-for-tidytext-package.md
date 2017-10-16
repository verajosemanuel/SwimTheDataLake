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

A clever friend of mine says: *the main programming language, is not Java or Python but English.*

So, when you're searching for help, you'll be much successful if searching in english. The main docs are in english, and if the topic is a bit obscure or not mainstream, you'll be lucky if there's some documents even in english. Searching for spanish documentation can lead you to bad translation if unlucky, or none at all at worst.

This issue is best known for all of us that had been working sometimes mining text. As you surely know, for a proper text analytics, text must be stripped of "non informative" tokens. Words like (in spanish): *de, la, que* are not very informative for the common tasks.

So, you started your Rstudio project, loaded tidytext library, and then, when reaching the point where you have to remove thast kind of words with a line like this:

```
df_text <- my_spanish_text %>% 
           unnest_tokens(word, text_line) %>%
           anti_join(stop_words)

```

Nothing happened but you won't notice that no token has been stripped. The reason is there's no spanish lexicon in tidytext package. What can we do?

One of the methods I've tested myself is to add your own stopwords. Instead of adding it all by hand you can get lists from some other sites like:

https://github.com/stopwords-iso/stopwords-es

http://countwordsfree.com/stopwords/spanish

Or you can add stopwords *borrowing* them from other text mining packages as **quanteda** or **tm**. Install those mentioned packages for the next chunk of code to properly work.

```
custom_stop_words <- bind_rows(stop_words,
                               data_frame(word = tm::stopwords("spanish"),
                                          lexicon = "custom"))
                                          
              # OR
                                          
custom_stop_words <- bind_rows(stop_words,
                               data_frame(word = quanteda::data_char_stopwords$spanish,
                                          lexicon = "custom"))
df_text <- df_text %>% 
    unnest_tokens(word, text) %>%
    anti_join(custom_stop_words) %>%
    count(word, sort = TRUE)

```


et voilà!  All spanish stopwords are out of the corpus and you can follow the next steps for text mining your data.

library(conflicted) library(dplyr) library(tidytext) library(syuzhet)
library(ggplot2) library(tidyverse) library(stringr) library(wordcloud)
library(conflicted) library(dplyr) library(tidytext) library(syuzhet)
library(ggplot2) library(tidyverse) library(stringr) library(wordcloud)
text.full \<- tibble(text = str_to_lower(full\$V4)) emotions \<-
get_nrc_sentiment(text.full\$text) emo_bar \<- colSums(emotions) emo_sum
\<- data.frame(count=emo_bar, emotion=names(emo_bar)) emo_bar
view(emotions) ggplot(emo_sum, aes(x = reorder(emotion, -count), y =
count)) ggplot(emo_sum, aes(x = reorder(emotion, -count), y = count)) +
geom_bar(stat = \'identity\') bing_word_counts \<- text.full %\>%
unnest_tokens(output = word, input = text) %\>%
inner_join(get_sentiments(\"bing\")) %\>% count(word, sentiment, sort =
TRUE) bing_top_10_words_by_sentiment \<- bing_word_counts %\>%
group_by(sentiment) %\>% slice_max(order_by = n, n = 10) %\>% ungroup()
%\>% mutate(word = reorder(word, n)) bing_top_10_words_by_sentiment %\>%
ggplot(aes(word, n , fill = sentiment)) + geom_col(show.legend =
FALSE) + bing_top_10_words_by_sentiment %\>% facet_wrap(\~sentiment,
scales = \"free_y\") + labs(y = \"Contribution to sentiment\", x =
NULL) + coord_flip()

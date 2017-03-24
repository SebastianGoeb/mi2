# Music Informatics Assignment 2
The melodies are provided in separate files.

To load the extended grammar:
?- [miNewExtended], [readfile].

To check if a melody is accepted by the grammar:
?- get_notes('accepted_1.abc',Input), tune(Input,[]).


# Question 1
## Sample Melodies
The melodies in the files accepted_1.abc, accepted_2.abc are accepted by the grammar, not_accepted_1.abc, not_accepted_2.abc give melodies that are accepted and not accepted respectively. In not_accepted_1 the first bar contains a dominant chord (ace) which is not accepted by the grammar in this position. In not_accepted_2 the last bar contains a melody that is not accepted by the grammar (d3Bd2) due to the note lengths.


# Question 2
## Explanation of Grammar
My extended grammar recognizes half bars instead of full bars in order to support 2 harmonies per bar. Each half bar allows any number of notes that add up to 3 (i.e. 111, 12, 21, 3) and most, but not all, support the by_x version of a harmony. These melodies are applied to the tonic, dominant and subdominant equally, allowing any harmony in any half bar with the exception of the first and last half bars.

## Sample Melodies
The files ext_accepted_1.abc and ext_accepted_2.abc contain melodies accepted by the extended grammar but not the original one. In the case of ext_accepted_1 the first bar contains the dominant harmony "ace" which is allowed in the extended grammar. In the case of ext_accepted_2 the first bar contains the melody "d3 a3" which is not supported by the original grammar but is supported by the extended grammar.

## Justification of Grammar
I wanted to allow greater variation in terms of melodies. That means more two harmonies per bar and more legal note lengths for each harmony. I also wanted to expand these capabilities to the dominant and subdominant harmonies because most music does restrict its melody to only the tonic. I opted not to implement more harmonies because many pieces, especially simple or traditional pieces, are built exclusively on I IV and V. I consider those harmonies adequate for most simple music and expanding into more harmonies or notes would lead the the grammar eventually accepting almost any mess of notes due to the overlap between the chords.


# Probabilistic Grammars
The paper claims that using probabilistic techniques from NLP could be applied to musical parsing. They show three different approaches whose performances ranges from completey unusable to correctly predicting over 80% of phrases. The worst performer is the Treebank Grammar with a Markov Grammar performing significantly better and an extended Markov Grammar performing slightly better still.

They claim that their probabilistic approach is superior to previous, more rigorous approaches because it is able to capture a greater variety of music structures. They also propose using their algorithm to speed up the otherwise time consuming process of annotating musical pieces by hand to help with future research into musical parsing.

I think a probabilistic approach such as this could be very useful to music generation. Markov processes can easily be modified to generate data based on likely sequences of notes which suggests that, after training with a certain style of music, this parser should also be able to generate music in that style. This would be very useful for composers wanting to generate music in a certain style. In the same way that the parser could speed up annotation with a little oversight, it could also produce music for the composer to use and apply finishing touches to. It could also serve as a way of quickly generating random melodies to serve as inspiration for manually composed pieces.

The downside of such a probabilistic is of course that one has essentially no control over what the algorithm learns. One does not control the internal model that it has of the style of music so it would be hard to make tweaks to the parser. The only way to modify it would be to re-train it with a different input and the final product would still be somewhat unpredictable, leading to a considerable amount of back and forth, attempting to perfect the parser.

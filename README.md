FlashOfUnAnimatedContent
========================

Core Animation bug rdar://problem/7311367

It is present in regular layer animation, layer backed view hierarchies (for example on window resize there will occasionally be a flash), and CSS3 Transitions in Safari 6.0.4 for OSX.

A demo using CSS3 Transitions can be seen here: http://jsfiddle.net/ZkuyR/

This project simply quickly and repeatedly adds a replacement animation with both a from and to value of the identity transform. There should not be any gaps of un-animated content between animations, but the red background is exposed occasionally. You might need to be watching a movie in the background for it to show.

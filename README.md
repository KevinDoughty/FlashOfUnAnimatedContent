FlashOfUnAnimatedContent
========================

Core Animation bug rdar://problem/7311367

It is present in regular layer animation, layer backed view hierarchies (for example on window resize there will occasionally be a flash), and CSS3 Transitions in Safari 6.0.4 for OSX 10.8.3.

A demo using CSS3 Transitions can be seen here: http://jsfiddle.net/ZkuyR/

This project quickly and repeatedly adds a replacement animation with both a from and to value of the identity transform. There should not be any gaps of un-animated content between animations, but the red background is exposed occasionally. You might need to be watching a full screen movie on a second monitor using a late 2011 13" MBP. Another example of the flash of un-animated content is my JellyBeans repo, which lays out many layers with the expensive corner radius and border.

The workaround is kCAFillModeBackward, which fills in the gaps.

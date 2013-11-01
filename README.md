FlashOfUnAnimatedContent
========================

Core Animation bug rdar://problem/12081774

It is present in regular layer animation, layer backed view hierarchies (for example on window resize there will occasionally be a flash), and I believe is the cause of CSS3 Transition flicker in Safari 6.0.4 for OSX 10.8.3 which can be seen here: http://jsfiddle.net/R6UW5/

This project quickly and repeatedly adds a replacement animation with both a from and to value of the identity transform. There should not be any gaps of un-animated content between animations, but the red background is exposed occasionally. You might need to be watching a full screen movie on a second monitor using a late 2011 13" MBP, or perhaps resize the window so it spans two monitors. This is the simplest regression, a more reliable example of the flash of un-animated content is my JellyBeans repo, which lays out many layers with an expensive corner radius and border.

The workaround is kCAFillModeBackward, which fills in the gaps.

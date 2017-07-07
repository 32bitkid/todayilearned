# Thoughts on `React.PureComponent` and `shouldComponentUpdate`

https://flexport.engineering/optimizing-react-rendering-part-1-9634469dca02`

This article is good but I do think his/her advice on `PureComponent` is misguided.

It, and more broadly `shouldComponentUpdate` are best implemented strategically in container-ish components, to optimize out descending down the tree.

Doing it everywhere means when one thing changes that _is_ deeply nested then you are incurring the cost of _checking_, which isn't feee, all the way down the stack.

The cost of determining if you _should_ render is wasted cost if it's always true.

So stopping as high up as you can, and letting lower components blindly render, because I wouldn't have have instantiated you unless I already _knew_ I needed to render is preferred

This point is echoed by this guy: https://news.ycombinator.com/item?id=14418576

^^^ this guy reacts
## @mixin
Here is how the mixin works. The definition and usage:
```scss
@mixin awesome {
    width: 100%;
    height: 100%;
}

body {
    @include awesome;
}
p {
    @include awesome;
}
```
The snippets above produce the following code.

```scss
body {
    width: 100%;
    height: 100%;
}
p {
    width: 100%;
    height: 100%;
}
```

To make the things a little bit more interesting we could make our mixin accepting parameters. 
Even better we are able to define default values if the mixin is called without arguments.
```scss
@mixin awesome($w: 100%, $h: 100%) {
    width: $w;
    height: $h;
}

body {
    @include awesome(960px);
}
p {
    @include awesome;
}
```
The result will be similar, but the width of the body is different.
```scss
body {
    width: 960px;
    height: 100%;
}
p {
    width: 100%;
    height: 100%;
}
```

## @extend
```scss
.awesome {
    width: 100%;
    height: 100%;
}

body {
    @extend .awesome;
}
p {
    @extend .awesome;
}
```
It's similar, isn't it. In SASS it looks almost identical, but in the CSS the result is:
```scss
.awesome, body, p {
    width: 100%;
    height: 100%;
}
```

Shorten then the version using a mixin. You can't pass parameters during the extending, but that's not the idea actually. @extend should be used in those places where you want to share properties between the elements.

The final code is still not perfect. That's because the .awesome class is also written in our final .css file. You may not use it at all, so it will be good if it is hidden. To achieve this you could use placeholders.

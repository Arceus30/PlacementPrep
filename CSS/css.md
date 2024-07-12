<a href="https://quickref.me/css3">Basic Sheet</a></br>

**Precedence**
if internal and external css are defined then the css which is defined later will override the css defined before
Inline CSS > Internal CSS == External CSS

**Specificity**
(!important) > Inline Styles > ID > (Classes = pseudo classes = attribute selector) > (Elements = pseudo elements)

css attribute with '!important' will override any other css applied to that selector
pseudo clases: :hover
attribute selectors: [href]
pseudo elements: ::before

**Units**

-   Absolute Units
    -   cm, mm, in, px, pt, pc
    -   **2.54cm = 25.4mm = 1in = 96px = 72pt = 6pc**
-   Relative Units

    -   em: Relative to the font-size of the element (2em means 2 times the size of the current font)
    -   ex: Relative to the x-height of the current font (rarely used)
    -   ch: Relative to the width of the "0" (zero)
    -   rem: Relative to font-size of the root element
    -   vw: Relative to 1% of the width of the viewport
    -   vh: Relative to 1% of the height of the viewport
    -   vmin: Relative to 1% of viewport's\* smaller dimension
    -   vmax: Relative to 1% of viewport's\* larger dimension
    -   %: Relative to the parent element

-   **Note** viewport dimensions does not accounts for scroll bars on the right and bottom

**Box Model**

-   ![Box Model](https://imgs.search.brave.com/bPah35-j48a-p2S3AMOPiDNhUARMu4tJy2wtmky4M9M/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9zdGF0/aWMuamF2YXRwb2lu/dC5jb20vY3NzcGFn/ZXMvaW1hZ2VzL2Nz/cy1ib3gtbW9kZWwu/cG5n)

-   Box-sizing attribute can take 2 values
    -   content-box: (default) all the width specified is taken by the content area and if border and padding are set then box will appear bigger than expected
    -   border-box: the width specified is taken by the entire box including border and padding

<a href="https://youtu.be/n4R2E7O-Ngo?t=10794&si=FJC24gNP06Qqmw0G">Float </a>

<a href="https://youtu.be/n4R2E7O-Ngo?t=11539&si=lK705OUlGp3BIyLL">Columns </a>

<a href="https://youtu.be/n4R2E7O-Ngo?t=12843&si=x0nhHHWRKsUmBYVz">Position </a>

<a href="https://youtu.be/n4R2E7O-Ngo?t=14246&si=5j5bh-9ivbrrfkLG">Flexbox</a>

<a href="https://youtu.be/n4R2E7O-Ngo?t=17166&si=AQ51bKvIYk9JIn2z">More on CSS images and background-images</a>

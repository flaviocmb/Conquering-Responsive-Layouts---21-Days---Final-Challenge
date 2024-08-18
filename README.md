# Conquering Responsive Layouts - 21 Days - Final Challenge
## Final Challenge Info

This challenge reinforces everything we've looked at.

Many parts of it are similar to what we've already seen, but there are a few sections that have some new twists. That said, everything in this challenge can be completed with what you've learned so far, and if you can make this page responsive, you're rocking it!

## A few considerations

I've only provided a desktop version of the design (except for one section). Despite this, I want you to take a mobile-first approach.

One of the most common reasons I hear as an excuse for writing desktop-first is that's what the design gives them. We've seen why we can still tackle things mobile-first despite that, so let's put it into practice!

The black box around the design is the viewport. The content inside should be limited to the max-width given in the design specs, but the backgrounds should extend to the edges of the viewport no matter the size.

The PDF outlines 2 specific breakpoints to use. You can modify them a little if you feel that it's appropriate, but you should aim for those ballparks.

Don't feel any shame in going back over previous lessons if you get stuck. The only rule is if you do have to go back, do not copy any paste any code that you've already written, or that you downloaded from my finished versions. You just spend 3-weeks at this, don't cheat yourself! Go and watch the video, and then code it yourself. Reinforce what you learned by writing it out again!

Have fun with this, and be proud of the progress that you've made!

(you'll get access to the solution eventually, but it's going to be awhile. I want to make sure you take a shot at it first)

# My style

I prefer to use this:

```css
.container {
    padding: 0 5%;
}
```

Over this:

```css
.container {
    margin: 0 auto;
    width: 90%;
}
```

The second approach cannot take background that extends from one side of the width to the other.

## position absolute

> ✍🏾 _Note: Absolute positioned elements are removed from the normal flow, and can overlap elements._

## span inside the `<button>`

```css
.hamburger {
    width: 50%;
    position: relative; 
    /* it's not necessary to use "position: relative;" coz we won't move the lines already centered */
}

.hamburger,
.hamburger::before,
.hamburger::after {
    width: 50%;
    display: block;
    margin: 0 auto;
    height: 3px;
    background: #FFF;
}
```

It is not necessary to use `position: relative;` because there is no need to move the hamburger lines; they are already centered.

Another important point about `<span>`: inline elements like `<span>` cannot have their dimensions adjusted by properties like **width** and **height** directly. In the code in question, `display: block;` is used on the `.hamburger` and its pseudo-elements, which makes them behave like block elements, allowing **width**, **height**, **margin**, and other properties to work as expected. Otherwise, they would not appear.

## the logo cannot be display block

If the block receives `display: block;`, it will take up the entire line and end up creating a `cursor: pointer`; on the whole line. Therefore, it is recommended to use `display: inline-block;`.

## Spacing of margin or padding on inline elements

I tried to apply margin or padding for spacing on inline HTML elements like the `<a>` tag in the footer, but I couldn't. I had to create classes for the list items: `about__item`, `other-things__item`, and `more__item`. See:

```css
<footer>
    <div class="container">
        <h2 class="footer_title">just scratching the surface</h2>
        <div class="about">
            <h3>About our company</h3>
            <p class="about__text">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
                minim veniam.
            </p>
        </div>
        <div class="around">
            <h3>Getting around</h3>
            <ul class="around__list">
                <li class="around__item"><a href="" class="around__list--link">Home</a></li>
                <li class="around__item"><a href="" class="around__list--link">About</a></li>
                <li class="around__item"><a href="" class="around__list--link">Contact</a></li>
            </ul>
        </div>
        <div class="other-things">
            <h3>Other things</h3>
            <ul class="other-things__list">
                <li class="other-things__item"><a href="" class="other-things__list--link">Lorem ipsum</a></li>
                <li class="other-things__item"><a href="" class="other-things__list--link">dolor</a></li>
                <li class="other-things__item"><a href="" class="other-things__list--link">sit amet</a></li>
                <li class="other-things__item"><a href="" class="other-things__list--link">consectetur</a></li>
            </ul>
        </div>
        <div class="more">
            <h3>And more</h3>
            <ul class="more__list">
                <li class="more__item"><a href="" class="more__list--link">Lorem ipsum</a></li>
                <li class="more__item"><a href="" class="more__list--link">dolor</a></li>
                <li class="more__item"><a href="" class="more__list--link">sit amet</a></li>
                <li class="more__item"><a href="" class="more__list--link">consectetur</a></li>
            </ul>
        </div>
    </div>
</footer>
```

So trying to apply anything to the `list--link` won't work!

An alternative would be to use `line-height` on the `<a>` elements, but I'm not sure if it's a good practice. To verify...

#### Three important conclusions:

- **padding** is generally the recommended practice for internal spacing on `<a>` elements, and **margin** for spacing between `<li>` elements.
- Turning links into block elements with `display: block;` is very useful for ensuring a larger clickable area and facilitating layout control.
- `line-height` can be used to adjust the height of text lines, but **padding** still offers more control over the clickable area.

## Very important about mobile first

It's important to note in this project how the `.row` class only appears from the media query above 700px. This way, we can use and reuse this class a lot. This ensures that the mobile version (below 700px) flows in columns without the need to use `.row`.
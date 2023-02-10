# Why TailwindCSS?

If you’ve never heard about TailwindCSS before, this cool open-source CSS utility framework speeds up your development process by a considerable amount. It’s directly written in the classes of your HTML, JSX, or TypeScript file.

So why would you use Tailwind instead of pure CSS or other frameworks?

### 1\. Perfect for beginners

It’s really easy to learn, the only previous knowledge you’re required to have is essential CSS. This is because Tailwind is derived from normal CSS code. For example, if you wanted to add horizontal padding to an element in CSS, you would write something like this:

```css
div {
 padding-right: 4px;
 padding-left: 4px;
/* or alternatively, */
 padding-inline: 4px;
}
```

In Tailwind, it’s rather easier. You just need to add a `px-1` to the element as a class name, like so:

```xml
<div class="px-1">Hello World!</div>
```

Easy-peasy right? I know! One thing that would greatly help your learning process is their [documentation](https://tailwindcss.com/docs/installation). The processes are well documented, and easy to understand and follow, which makes it the best documentation I’ve ever seen and used in all areas including User Interface, usefulness, and accessibility.

### 2\. Responsiveness at its peak

Tailwind comes with pre-defined CSS classes that can be quickly used to create a responsive design. These classes can be used to create fluid layouts without having to write custom CSS code. They can also be combined to create more complex layouts.

Additionally, Tailwind provides a set of pre-defined media queries that can be used to make certain elements or layout changes based on screen size. For example, if you wanted to change the orientation of an element (in this case, a `div`) from a column view on mobile screens to a row view when it’s on a tablet screen, your code would look like this:

```xml
<div class="flex-col sm:flex-row">
/* the 'sm' here stands for any screen width above 640px */
    <h1>This is a heading</h1>
</div>
```

One thing to note is that Tailwind is mobile first. This means that styles are easier applied to small/mobile screens first before expanding to larger screens. [60% of the traffic on popular websites is gotten from mobile devices](https://www.statista.com/statistics/277125/share-of-website-traffic-coming-from-mobile-devices/), so if you want to retain the rate at which users visit your site, you would like to pay attention to mobile responsiveness.

### 3\. Design System out of the box

Who doesn’t want a framework that gives you a complete color pallet including their respective shades, industry-standard screen breakpoints, typography, and easy dark mode configuration without extra code? Not you. Tailwind takes care of those base things while you can focus on making your web application more functional.

![Tailwind color palette](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j623fwvgbcw9op3zkyzq.png align="center")

## Conclusion

You’ve seen 3 different reasons you should switch; it's simple to understand, it improves responsiveness, and it provides you with a design system. There are many others apart from the ones listed here, which you will discover when you start using the framework.

## Resources

* [Get started with Tailwind CSS](https://tailwindcss.com/docs/installation)
    
* [What is Tailwind CSS? A Beginner's Guide](https://www.freecodecamp.org/news/what-is-tailwind-css-a-beginners-guide/)
## I joined a Twitter challenge...

Just before the weekend I saw a tweet from [Gift](https://twitter.com/codingossy/status/1565239107034439681?t=kBAVzGsASdXAe7PhFWmQ-A&s=19) about a frontend challenge that'd run from September 1st to September 15th. We're to recreate a Cryptocurrency landing page from a slightly complicated figma design. Once I saw the tweet, I just knew I had to hop on it because, why not? I've never joined an online challenge before and I don't exactly post stuffs I've built (for some undertermined reason). This had to be the motivation, inspiration and external push I needed to start putting myself out there. So I did it :-)

### what I built...

Well basically it's a landing page of a fictional cryptocurrency website gotten from the Figma Open Source Design community. Some of the 'features' are:

- responsiveness across multiple screen sizes
- some very sleek scroll and fade animations (yeah I'm proud of myself for actually implementing those:))
- making sure that the implementation looks as closely as possible to the figma designs

Yeah not too many features as expected right? Well there were somethings I did to get the result looking pretty cool.

### the process...

So I built this project with HTML and TailwindCSS mainly, then a sprinkle of JavaScript. Now when I say sprinkle I really mean it because there's probably not more than 20 lines of code on there.

The fade-in scroll animations are powered by a lightweight JavaScript library called [ScrollReveal](https://scrollrevealjs.org). Pretty cool and intuitive, you should check it out if you haven't.

### some stuffs I learnt along the way


1. **AOS Library**: If your script is internal, you need to place it just before the closing `body` tag. If you're using an external JS file, add 'defer' to  the script attributes (this waits for all the DOM elements to load before executing the JS file) . This prevents a null reference error because JavaScript executes from top to bottom and as at the time of calling the AOS Library, the DOM hasn't finished loading all the content.

2. **Image Filtering**: If you're not too familiar with manipulating SVGs, you can change the color of your icon or image on hover using the CSS `filter` selector. I found [this very helpful tool](https://isotropic.co/tool/hex-color-to-css-filter/) for converting your target color to the CSS `filter` equivalent. ****The downside of this tool though, is that it's built to convert from black to your preferred color. So if you're converting anything other than black, I found a 'quite stressful but worth it' hack you can try:
  - when you convert to your target color, test it to see which color it displays
  - try to visually imagine (or use a color picker) the closest color it displays, and then use the tool to convert it again. It should look closer to what you're trying you achieve
  - if it looks close enough but you need perfection (which might just be impossible in this case unless you happen to be a cyborg with advanced eyesight), play around with the `brightness` and `saturation` value until you're satisfied.

I probably need to point out that all these steps aren't really necessary if you are working with a black image or SVG. Also if you're knowledgeable enough, you can use 2 different images/SVGs just decide to dynamically change the `src`.

And if the steps aren't clear enough, I'd write a standalone article about it, if you'll read :)

### things I'm yet to figure out

I was trying to get the `body` tag from the DOM and add a class to it when the navbar is active. For some reason, `getElementsByClassName` didn't work. However, `getElementById` worked and I have no idea why. Here's the error:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662771517670/AbALM2vxO.png align="left")

There's probably something I've not learnt yet or missing out, but I'm pretty sure I'll get there.

### the final result, as promised :-)

%[https://www.loom.com/share/ede05bb3c4e3466ea6a6f298fdc44fb7]

You can access the live project [here](crappocryptochallenge.netlify.app) and GitHub repository [here](https://github.com/CyberGeni/crappo/)

okay bye
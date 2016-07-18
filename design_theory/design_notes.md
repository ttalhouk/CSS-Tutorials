# Elements of Design

1. Audience
  * age, sex, gender, social considerations
2. Tone
  * Casual, formal, humorous?
3. Purpose
  * informational, conversational

## Typography

Create a style guide.

Set Headline text, navigation text, sub headings, body text, etc..  
This helps keeping it consistant throughout the document.

**Fonts**

*Serif*

Humanist serif:  
Emulates calligraphy and is classical and traditional.  
Transitional serif:  
Sharp serifs, strong stylish and dynamic typical in legal or academic look  
Modern serif:  
Thin horizontal serif high contasting thick and thin sides good for art and culture applications  
Slab serif:  
Heavy thick serifs with little contrast authoritative but friendly  

*Sans-Serif*
Humanist sans-serif:  
Emulates calligraphy and typically used for government work.  
Transitional sans-serif:  
Unassuming and modern.  Good for technology and transporational work.  
Geometric sans-serif:
Geometric shapes make up the backbone for the letters.  Strict and objective.  Typically used for science or architecture.

*Script*  
Mimics handwriting and calligraphy

Gives a humanistic touch but not good for body copy as it can be hard to read.

*Typical Layout*  
Basic layout consists of Serif font for Headlines and sub headers, and sans-serif for body copy.  
Notes:  
* Don't use same style from serif and sans-serif in same document such as humanist on both. Makes it look similar and indistinguishable.  
* Don't choose two fonts from the same Class such as two serif fonts or two sans-serif fonts.  
* Look for contrast in style  
* Use web-licensed fonts  

## Step 2 sizes

Users need some guidence to quickly discern how to navigate.  Usually go from biggest to smallest for context. For body copy typically use 16px body copy font.  Headline is typically 200-300% of body copy.  Body Heading is typically 150% and navigation is typically 100% body copy size.  By line typically 75% of body copy.  

**Leading**  
Leading is the space between lines.  Too large negatively affects readability.  Too tight can cause a claustrophobic feel.  Typical leading is 120-150% of body copy size.  This can be accomplished with CSS.  
`line-height: 1.5;` // 150% height.  

**Use of Bold or Italics**  
Too much bold muddies the type and makes it confusing what is important.  Also users expect bolder font for heading so using thin font for heading and bold fonts for body is not recommended.  

## Line Width and Window  

Line width is measured in characters per line.  Good rule of thumb is 50-70.  This is controlled in CSS using `max-width` property.  This needs to be adjusted to try and aim for the 50-70.  

Minimize leaving one word in a line or one line in a group as it disrupts the flow.  Adust font size, leading, and width to try an fix.  Must insure headlines are widow free.
```
Some Headline With A Widow On Second
Line //<-- Don't do this
```
## Color Theory

Light is processed using RGB.  All colors mixed create white.  Humans process in HSL which stands for Hue, Saturation, and Lightness.   

*Hue* is best represented in a color wheel.  
*Saturation* is the percentage of color in the image.  100% is pure color, 0% is gray.  
*Lightness* is the amount of light in a color.  100% is white, 0% is black.  Color is a gradent within that ~50%  

**Color Scheme**  
5 colors to base the site around.  

*Step 1*  
Select a Base Color based on Mood.  
* Red: color of Heat, Passion, Excitement  
* Blue: color of Security, Truth, Stability, implies Loyalty, Reliability, Open Communication
* Orange: color of Warmth, Vitality, associated with Reliability and Playfulness  
* Yellow: color of Optimism, Creativeness  
* Green: color of Serenity, Health, Growth, Nature, Freshness  
* Purple: Spirituality, Wealth, Intelegence  
* Pink: Youthful, Intensity  
* Brown: Duriblity, Class  
* Black: Power, Drama, Bold, Strong  
* White: Simplicity, Clean

*Step 2*  
Build scheme from base  
* Monochromatic: Constant Hue, varied in statuation and lightness  
* Analogous: Varying Hue to colors next to it on the wheel  
* Complimentary: Has colors of the same and opposite Hue within the set  

**Color and Type**  
Typography must have high contrast between the type and background. Contrast can be done using hue, lightness and saturation.  Typically multifacited differences are required such a hue and lightness.  The standard for contrast is in the WCAG 2  *Website Content Accessibility Guidelines*  

Optimal is High contrasting Lightness (black/white).  
Secondary is same hue but highly different lightness and saturation  

Red/Green and Blue/Orange are hard for humans to differentiate.  

Warm colors appear closer so use them in the forground and cool in the back.

## Basic layout

Since many read left to right top to bottom branding and Logo's should appear in the upper left. Next consideration is navigation.  Navigation with a small amount of items is ideal for a horizontal navigation scheme, otherwise a vertical scheme may be better but not used often so you need to have a good reason to use it.  Footer should always span the entire width of the page.  

**The Grid**  
Vertical columns with gutters inbetween establish columns in which content is to be placed.  Horizontal baselines are to keep the vertical content flow correct but may be difficult to implement on the web.  Fluid grids drop/add columns as needed when screen size grows or shrinks.

**Whitespace and Balance**  
Whitespace allows for area to be open and free so as to not feel cluttered.  Ballance can be achieved using symetry.  Acentric content can drive attention and break monotony but should still adhere to the grid and whitespacing to give an overall ballance.

**Resources**  
* Smashing Magazine
* .Net Magazine
* Thinking With type
* Elements of Typograpic Style
* Golden Ratio Typography calculator
* Gridpak 

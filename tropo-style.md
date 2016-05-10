# The Crossroads of Styling Troposphere
We know we can do much better. A re-factor is necessary which is a great opportunity to do things the way we want. So... what do want to do? 

In the attempt to help organize the decision, here is a list of general considerations and requirements, as well as some pros and cons of the more appealing options.

## Considerations and Requirements

#### Best Practices:
- Naming conventions
- Style linting
- Managing scope
- Element decoupling
- Staying DRY

#### Can Support:
- Theming
- Modularity
- Easy to maintain

#### Can Use:
- Autoprefixing
- Media queries
- Easy interactions syntax (:hover, :focus, etc...)
- Animations
- Variables

### Possible Technical Debt
- Build steps
- New syntax
- Dependencies
- How difficult is it to change?
- Available documentation?
- How well supported?

## Vanilla CSS VS. Vanilla In-line Styles
Long standing has been the notion that inline styles are a bad practice. However, with an app that renders entirely with JS many of the arguments against inline styles are not as relevant. Though some downsides still remain a consideration, there are many compelling reasons to use them over CSS. At the same time, there are many valid arguments against CSS that inline styles or CSS modules can solve. 

Although there are many tools to help solve the issues with either option, many pros and cons are left to evaluate. Below is a list comparison of the three options for styling augmented with tools to smooth over some of the inherent short comings. 

Here is an older yet insightful presentation on Facebook's path to [adopting inline styles](https://speakerdeck.com/vjeux/react-css-in-js) into their app.   
Here is a video from Colin Megill _(Contributer to Radium)_ about [why his company switched to inline styles](https://www.youtube.com/watch?v=NoaxsCi13yQ&list=PLtAB5E0_yWtrSN3Ta-s4nHPnlYUc911Y0&index=1).

## Options for styling
There are a lot of options and tools for styling applications these days, however these are the three I feel are the most practical, well adopted, and offer the most for our needs.
### CSS with PostCSS
[PostCSS Docs](https://github.com/postcss/postcss)  
_(text in **bold** is provided by a postCSS plugin)_ 
#### Pros:
- psuedo elements
- Easier to stay DRY (cascade)
- Caches in header
- Mature best practices
- Broad Familiarity 
- **More tools**
- **Can use Reset**
- **Access to an infinite number of utilities**
    - **Converting px to ems**
    - **StyleLint**
- **Growing user base**

#### Cons:
- Less modular than in-line
- Global namespace
- Depends on a great deal of discipline
- Assumes a structure in html without being able to describe it
- Hard to know what elements are affected by a rule 
- Hard to know how styles are affecting a given element
- No real-time computation of values
- Unclear implementation of expected HTML structure
- Components are not packaged
- More complicated configuration
- Using Reset helps with specificity wars but we still have global class names
- Using Reset requires explicit declaration
- Using Reset creates a large amount of extra CSS

### CSS Modules with PostCSS
[Article on CSS Modules](http://www.sitepoint.com/understanding-css-modules-methodology/)    
[PostCSS Loader](https://github.com/outpunk/postcss-modules)  
_(text in **bold** is provided by a postCSS plugin)_ 
#### Pros:
- pseudo elements
- Easier to stay DRY (cascade)
- Caches in header
- Mature best practices
- Broad Familiarity 
- **More tools**
- **Can use Reset**
- **Access to an infinite number of utilities**
    - **Converting px to ems**
    - **StyleLint**
- **Growing user base**
- Components are packaged 
- Name spacing is solved

#### Cons
- Assumes a structure in html without being able to describe it
- No real-time computation of values
- Unclear implementation of expected HTML structure
- More complicated configuration
- Less familiar 
- Possibly lose some features of PostCSS like px to ems 
- Theming becomes awkward
- Inspecting with devtools seems rough because of generated class names
- Better but still hard to  know what elements are affected by a rule
- Better but still hard to know how styles are affecting a given element
- Better but still requires discipline 

### Inline Styles with Radium
[Radium Docs](https://github.com/FormidableLabs/radium)  
_(text in **bold** relates to Radium)_  
#### Pros:
- Very modular
- No global variables
- Depends less on discipline
- Easier to see the affects of what you change
- Easy to know how styles are affecting a given element
- Easy to maintain (eliminate dead code)
- Real-time computation of values
- Clear implementation of expected html structure
- Less complicated to use (not a build concern)  

**These are obviously available in CSS but worth noting Radium adds them to inline**
- **More familiar / convenient syntax for things like :hover**
- **Media queries** 
- **Autoprefixing**

#### Cons 
- No pseudo elements :before, :after, :nth-child etc.
- No caching like with CSS (a bigger issue with server side rendering)
- Takes a performance hit but not noticeable with react DOM speed and will no doubt change as JS DOM and inline style adoption grows
- Less familiar
- A bit kludge looking in components _(however comforting in the clarity of what is happening and why)_
- Less tools than postCSS but growing and easier to write on the fly since it's JS
- No linting (Yet)

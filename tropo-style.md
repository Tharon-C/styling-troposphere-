# The Crossroads of Styling Troposphere
We know we can do much better. A re-factor is necessary which is a great opportunity to do things the way we want. The question is what do we want to do? I have a lot of opinions and have gone through some pros and cons of the more appealing options, in the attempt to help organize the decision. 

These are my notes listing the considerations and the pros and cons of the various approaches available. 

## Considerations
We don't necessarily have needs that are particularly unique however it may be helpful when evaluating an option to consider some of our needs

### Troposphere Requirements

#### Best Practices:
- Naming Conventions
- Formating Style Guide
- Managing Scope
- Element decoupling
- Being DRY

#### Can Accommodate:
- Theming
- Modularity
- Easy to maintain

#### Can Support:
- Autoprefixing
- Media Queries
- Easy Interactions syntax (:hover, :focus, etc...)
- Animation
- Variables

### Possible Technical Debt
- Build Steps
- New syntax
- Dependencies
- How difficult is it to change?
- Available Documentation?
- How supported?

## Vanilla CSS VS. Vanilla In-line Styles
There are many valid arguments against CSS and some new compelling arguments for inline styles.
Although there are many tools to help solve issues with either option here is a brief overview of each without these tools.

Here is an older yet insightful presentation on Facebook's path to [adopting inline styles](https://speakerdeck.com/vjeux/react-css-in-js) into their app.   
Here is a video from Colin Megill _(Contributer to Radium)_ about [why his company switched to inline styles](https://www.youtube.com/watch?v=NoaxsCi13yQ&list=PLtAB5E0_yWtrSN3Ta-s4nHPnlYUc911Y0&index=1).
### In-line Styles
#### Pros:
- Very modular
- No global variables
- Depends less on discipline
- Easier to see the affects of what you change
- Easy to know how styles are affecting a given element
- Easy to maintain (eliminate dead code)
- Real-time computation of values
- Clear implementation

#### Cons:
- No media queries
- No psuedo element syntax (:hover, :focus, etc …)
- Harder to stay DRY
- Can look messy in a component file

### CSS
#### Pros:
- Has media queries
- psuedo elements
- Easier to stay DRY
- Caches in header
- More tools
- Mature Best Practices

#### Cons:
- Less modular than in-line
- Global Namespace
- Depends on a great deal of discipline
- Assumes a structure in html without being able to describe it.
- harder to know what elements are affected by a rule 
- Hard to know how styles are affecting a given element
- No real-time computation of values
- Unclear implementation

## Options for styling
There are a lot of options and tools for styling applications these days, however these are the three I feel are the most practical, well adopted, and offer the most for our needs.
### Traditional CSS with PostCSS
[PostCSS Docs](https://github.com/postcss/postcss)
#### Pros:
- Broad Familiarity 
- Can use Reset now
- Access to an infinite number of utilities.
    - Converting px to ems
    - StyleLint
- Growing user base

#### Cons:
- No real-time Computation of values
- Components are not packaged
- More complicated configuration
- Using Reset helps with specificity wars but we still have global class names
- Using Reset requires explicit declaration
- Using Reset creates a large amount of extra CSS
- Assumes a structure in html without being able to describe it.
- Although better, still:
    - harder to know what elements are affected by a rule 
    - harder to know how styles are affecting a given element
    - requires discipline 

### CSS Modules with PostCSS
[Artical on CSS Modules](http://www.sitepoint.com/understanding-css-modules-methodology/)    
[PostCSS Loader](https://github.com/outpunk/postcss-modules)
#### Pros:
- Same as Traditional with PostCSS
- Components are packaged 
- Name spacing is solved

#### Cons
- Less familiar 
- No real-time computation of values
- Possibly lose many features like px to ems, variables etc... 
- Even more complicated 
- Theming becomes awkward
- Assumes a structure in html without being able to describe it.
- Inspecting with devtools is rough because of generated class names
- Although much better, still:
    - harder to know what elements are affected by a rule 
    - harder to know how styles are affecting a given element
    - requires discipline 

### Inline Styles with Radium
[Radium Docs](https://github.com/FormidableLabs/radium)
#### Pros:
- Same as inline 
- More familiar syntax for things like :hover
- Media queries 
- Autoprefixing
- Less complicated to use (not a build concern)

#### Cons 
- No caching like with CSS
- Although better still less familiar
- A bit kludge looking in components _(however comforting in the clarity of what is happening and why)_
- Less tools than postCSS but growing and easier to write on the fly since it's JS
- No linting (Yet)

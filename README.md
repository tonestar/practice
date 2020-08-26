# Practice project

For this layout/setup I decided to go very simple – no js and no state management so no need for react. I used NPM as a task runner/package installer to compile scss but nothing more.

The compiler can be run by installing npm and typing `npm run scss` in your terminal.

In terms of the sass structure, I decided to follow a pattern that keeps components, global settings, and vendor files separate. The folder are `Components` – relates to the component, `Variables` for global settings, and `Vendor` for third party. In this case, I am just using naturalize to set a nice baseline to style over.

SCSS style-wise I am using a semi-BEM style that I am comfortable with – initially Pascal-case and then camel case for subsequent elements. I also use hypens exclusively vs underscores as I don't like them. For modifiers I simply use `--`. The reason I use this style is that it meshes in nicely with a React based paradigm, as those components are Pascal-case.

Also, I am a fan of the `&-something` style as I think it forces the coder to keep their hierarchies flat – if it's getting nested and confusing, it's probably time to make new components instead. However, there's also a good argument that it hurts searchability so most often I instead write the full class. I thought I had to pick one approach for this exercise so I chose my favourite.

Typography I have chosen to use fluid typography that scales both line-height and font-size relative to the width of the viewport. I like this approach as it provides a seamless responsive experience with minimal designer/developer input, particularly in the middle tablet sized breakpoint areas where it can be difficult to anticipate where the design will break.

In terms of layout I have opted to use CSS Grid. This has partial, polyfilled support for IE11 and since Microsoft has officially sounded the deathknell I felt it appropriate to use this approach.

In terms of Git I am going with git-flow, with a Master, Develop, Feature, and UAT branch.

For design, I chose almost offensively bright colours and added a bit of flair by skewing elements.


## Box model

The box model is the core paradigm of layout in  css. It provides the coder with a set of consistent rules of how elements on a page can be placed.
Central to the box model is the intrinsic height and width of an element. Each layer of the box model is like an onion, wrapping this central core.

The next layer around the core is padding. This is used to provide the first layer of spacing around the core, and provides a fairly robust and 'safe' method of allowing space around the element. This will contribute to the actual size of the element – useful for increasing the clickable area of links or buttons for example.
The next wrapping layer around the core and padding is border. This provides a way of defining the outline or edges of an element. This has a myriad of different options in displaying the edges.
The outer wrapping layer is margin. This is best thought of the layer that defines the spacing between elements. Margin has special properties in respect to padding in that it can be a negative value to pull elements closer, can 'collapse' when two elements are placed next to each other in certain circumstances – the latter being a useful tool when defining spacing rules between typographic elements.

## JS Questions

```const sales = [
  {
    itemSold: 'Football',
    price: 19.99,
    dateSold: '2018-04-07',
    id: 'j_123',
  },
  {
    itemSold: 'Trainers',
    price: 159.95,
    dateSold: '2018-03-02',
    id: 't_acds1',
  },
  {
    itemSold: 'Cricket bat',
    price: 204.97,
    dateSold: '2018-04-05',
    id: 'j_456',
  },
  {
    itemSold: 'Rugby ball',
    price: 30.00,
    dateSold: '2017-04-22',
    id: 't_acds3',
  },
  {
    itemSold: 'Hockey stick',
    price: 54.95,
    dateSold: '2017-03-19',
    id: 'j_999',
  },
];
```

1. Return the sum of the price of all properties as a single value.

```
const sum = sales.map(item => item.price).reduce((total, price) => total + price);
```

2. Return the items which were sold in 2017.
```
const yearSorted = sales.map(item => item).filter((product) => (
  new Date(product.dateSold) <= new Date('2018-01-01')
));
```

3. Return an array of all of the itemsSold properties as strings, sorted alphabetically.

```
const itemSorted = sales.map(item => item.itemSold).slice().sort(); // Slice to not muck around with original array  
```

4. Using id as an argument, return the sale which matches the id.

```
const saleById = (id) => (
   sales.map(item => item).filter(item => item.id === id)
)

```
Calling the functions
```
console.log(sum)
console.log(yearSorted);
console.log(itemSorted);
console.log(saleById('t_acds1'));
```

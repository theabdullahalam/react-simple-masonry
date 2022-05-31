# React Simple Masonry
Standalone simple masonry component for rendering responsive masonry layouts.

## Installation
```shell
npm i react-simple-masonry
```

## Usage
### With HTML Elements
#### Straightforward
Simply wrap your elements with the `<Masonry>` component, and you should get a three-column masonry layout, with a gap of ```1rem``` between the columns.
```jsx
<Masonry>
  {
    images.map((url, i) => <img src={url} key={i} />)
  }
</Masonry>
```

#### Number of columns

To change the number of columns, pass in a `columnCounts` object with a default value - 
```jsx
<Masonry columnCounts={{ default: 4 }}>
  {
    images.map((url, i) => <img src={url} key={i} />)
  }
</Masonry>
```

#### Different columns for different screen sizes

To specify the number of columns to show up till particular breakpoints, pass in a `columnCounts` object with the breakpoints you need, and a default value. The breakpoints are equivalent to `max-width` media queries -

```jsx
<Masonry 
  columnCounts={
    { 
      600: 1, 
      800: 2, 
      1000: 3, 
      default: 4 
    }
  }
>
  {
    images.map((url, i) => <img src={url} key={i} />)
  }
</Masonry>
```

#### Gap between columns

To specify the size of the gap between columns - 

```jsx
<Masonry 
  columnCounts={
    { 
      600: 1, 
      800: 2, 
      1000: 3, 
      default: 4 
    }
  }
  columnGap="2rem"
>
  {
    images.map((url, i) => <img src={url} key={i} />)
  }
</Masonry>
```

### With Custom Components
Rendering custom components is similar to how one would render regular elements, except that the component must add the style passed in by the `Masonry` component.

For example, if your implementation looks like this:

```jsx
<Masonry 
  columnCounts={
    { 
      600: 1, 
      800: 2, 
      default: 3
    }
  }
  columnGap="1rem"
>
  {
    images.map((url, i) => <MyComponent url={url} key={i} />)
  }
</Masonry>
```

then your `MyComponent` component must do this:
```jsx
// accept masonry_item_style among other props...
export function MyComponent({masonry_item_style}){
  // ...your code
  return (
    // you can add your own styles after masonry_item_style like so
    // style={{
    //      ...masonry_item_style, 
    //      background: "wheat", 
    //      ...etc 
    //   }}
    <div style={{...masonry_item_style}}>
      // ...rest of the component
    </div>
  )
}
```
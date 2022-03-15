# The `sx` prop

sx属性

The `sx` prop is a shortcut for defining custom style that has access to the theme.

sx属性对主题进行自定义样式一个捷径。

The property is a superset of CSS that packages [all the style functions](https://mui.com/system/basics/#all-inclusive) that are exposed in `@mui/system`. You can specify any valid CSS using this prop.

这个属性是 从@mui/system 暴露出的包的css的一个超集，你可以用这个属性设置任意合法的css

## Example



{{"demo": "Example.js", "bg": true, "defaultCodeOpen": true}}





On the example above, you can notice that some of the values are not valid CSS properties.

在上面的例子里，你可以发现有些值并不是合法的css，

 

This is because the `sx` keys are mapped to specific properties of the theme.

 这是因为sx的键值，是从主题的特有的属性映射过来的。

In the following sections, you will learn how different `sx` properties are mapped to specific parts of the theme.

在下面的章节中，你将学会区分sx属性与主题的特有属性的映射的不同之处

## Theme aware properties ？？？

### Borders

边界

The `border` property can receive only a number as a value.

 边界这个属性只能接收一个数字作为值

It creates a solid black border using the number as the width.

它使用这个数字作为宽度来创建实心的黑色边

```
<Box sx={{ border: 1 }} />
// equivalent to border: '1px solid black'
```



The `borderColor` property can receive a string, which represents the path in the `theme.palette`.

borderColor属性能接收一个包含默认路径theme.palette的string，

```
<Box sx={{ borderColor: 'primary.main' }} />
// equivalent to borderColor: theme => theme.palette.primary.main
```



The `borderRadius` properties multiples the value it receives by the `theme.shape.borderRadius` value (the default for the value is `4px`).

borderRadius属性乘上它接收到的theme.shape.borderRadius（它默认值是4px）

```
<Box sx={{ borderRadius: 2 }} />
// equivalent to borderRadius: theme => 2 * theme.shape.borderRadius
```



Head to the [borders page](https://translate.mui.com/system/borders/) for more details.

去到borders page能获得更多详情

### Display



The `displayPrint` property allows you to specify CSS `display` value, that will be applied only for printing.

显示打印参数，在用来打印时，允许你指定css display的值，

```
<Box sx={{ displayPrint: 'none' }} /> // equivalent to '@media print': { display: 'none' }
```



Head to the [display page](https://translate.mui.com/system/display/) for more details.

去到display page能获得更多详情

### Grid

网格

The grid CSS properties `gap`, `rowGap` and `columnGap` multiply the values they receive by the `theme.spacing` value (the default for the value is `8px`).

网格css的属性：如gap， rowGap 和 columnGap的属性会乘上他们从theme.spacing接收到的值（默认值是8px）

```
<Box sx={{ gap: 2 }} />
// equivalent to gap: theme => theme.spacing(2)
```



Head to the [grid page](https://translate.mui.com/system/grid/) for more details.



### Palette

调色板

The `color` and `backgroundColor` properties can receive a string, which represents the path in the `theme.palette`.

颜色和背景色属性可以接收到一个字符串，这个字符串会加上theme.palette路径。

```
<Box sx={{ color: 'primary.main' }} />
// equivalent to color: theme => theme.palette.primary.main
```



The `backgroundColor` property is also available through its alias `bgcolor`.

背景属性可以写成它的别名bgcolor

```
<Box sx={{ bgcolor: 'primary.main' }} />
// equivalent to backgroundColor: theme => theme.palette.primary.main
```



Head to the [palette page](https://translate.mui.com/system/palette/) for more details.



### Positions

位置

The `zIndex` property maps its value to the `theme.zIndex` value.

zIndex属性映射来自theme.zIndex的键值

```
<Box sx={{ zIndex: 'tooltip' }} />
// equivalent to zIndex: theme => theme.zIndex.tooltip
```



Head to the [positions page](https://translate.mui.com/system/positions/) for more details.



### Shadows

阴影

The `boxShadow` property maps its value to the `theme.shadows` value.

盒阴影的属性映射它的值到theme.shadows上

```
<Box sx={{ boxShadow: 1 }} />
// equivalent to boxShadow: theme => theme.shadows[1]
```



Head to the [shadows page](https://translate.mui.com/system/shadows/) for more details.



### Sizing

尺寸

The sizing properties: `width`, `height`, `minHeight`, `maxHeight`, `minWidth` and `maxWidth` are using the following custom transform function for the value:

尺寸属性包括：`width`, `height`, `minHeight`, `maxHeight`, `minWidth` and `maxWidth` 使用下面的转换方式

```
function transform(value) {
  return value <= 1 ? `${value * 100}%` : value;
}
```



If the value is between [0, 1], it's converted to percent.

 如果属性在0和1之间，则装换成百分比属性

Otherwise, it is directly set on the CSS property.

否则，直接设置成css属性

```
<Box sx={{ width: 1/2 }} /> // equivalent to width: '50%'
<Box sx={{ width: 20 }} /> // equivalent to width: '20px'
```



Head to the [sizing page](https://translate.mui.com/system/sizing/) for more details.



### Spacing



The spacing properties: `margin`, `padding` and the corresponding longhand properties multiply the values they receive by the `theme.spacing` value (the default for the value is `8px`).

间距属性：margin，padding 和 书写属性 会乘上theme.spacing的值（默认为8px）

```
<Box sx={{ margin: 2 }} />
// equivalent to margin: theme => theme.spacing(2)
```



The following aliases are available for the spacing properties:

下面是一些间距属性的简写

| Prop | CSS property                    |
| ---- | ------------------------------- |
| `m`  | `margin`                        |
| `mt` | `margin-top`                    |
| `mr` | `margin-right`                  |
| `mb` | `margin-bottom`                 |
| `ml` | `margin-left`                   |
| `mx` | `margin-left`, `margin-right`   |
| `my` | `margin-top`, `margin-bottom`   |
| `p`  | `padding`                       |
| `pt` | `padding-top`                   |
| `pr` | `padding-right`                 |
| `pb` | `padding-bottom`                |
| `pl` | `padding-left`                  |
| `px` | `padding-left`, `padding-right` |
| `py` | `padding-top`, `padding-bottom` |



Head to the [spacing page](https://translate.mui.com/system/spacing/) for more details.



### Typography

字体排版

The `fontFamily`, `fontSize`, `fontStyle`, `fontWeight` properties map their value to the `theme.typography` value.

字体，字体撒小，字体样式，字体粗细的属性会映射到theme.typography的值

```
<Box sx={{ fontWeight: 'fontWeightLight' }} />
// equivalent to fontWeight: theme.typography.fontWeightLight
```



The same can be achieved by omitting the CSS property prefix `fontWeight`.

可以省略类似fontWeight的前缀

```
<Box sx={{ fontWeight: 'light' }} />
// equivalent to fontWeight: theme.typography.fontWeightLight
```



There is an additional `typography` prop available, which sets all values defined in the specific `theme.typography` variant.

有些附加的排版属性，在theme.typography上设定的各种属性，都是可以使用的。

```
<Box sx={{ typography: 'body1' }} />
// equivalent to { ...theme.typography.body1 }
```



Head to the [typography page](https://translate.mui.com/system/typography/) for more details.



## Responsive values

响应值

All properties as part of the `sx` prop also have a support for defining different values for specific breakpoints.

 所有sx的属性都支持指定断点来获得不同的值

For more details on this, take a look at the [Responsive values section](https://translate.mui.com/system/basics/#responsive-values).

想要获得过更多的信息，请看[Responsive values section](https://translate.mui.com/system/basics/#responsive-values).

## Callback values

返回值

Each property in the `sx` prop can receive a function callback as a value.

 每一个sx属性，可以接收一个函数返回值作为参数

This is useful when you want to use the `theme` for calculating some value.

这对你想用theme来计算某些值很有帮助

```
<Box sx={{ height: (theme) => theme.spacing(10) }} />
```



`sx` can also receive a callback when you need to get theme values that are object:

sx还可以接收一个以theme的值组成的对象作为返回值

```
<Box
  sx={(theme) => ({
    ...theme.typography.body,
    color: theme.palette.primary.main,
  })}
/>
```

## Array values

数组值

Array type is useful when you want to partially override some styles in the former index:

当你想部分覆盖一些就样式时，数组类型是有用的；

```
<Box
  sx={[
    {
      '&:hover': {
        color: 'red',
        backgroundColor: 'white',
      },
    },
    foo && {
      '&:hover': { backgroundColor: 'grey' },
    },
    bar && {
      '&:hover': { backgroundColor: 'yellow' },
    },
  ]}
/>
```



When you hover on this element, `color: red; backgroundColor: white;` is applied.

当鼠标移到这个元素上时，color: red; backgroundColor: white;  将被应用



If `foo: true`, the `color: red; backgroundColor: grey;` is applied when hover.

如果foo为true时，color: red; backgroundColor: grey 将在hover时生效



If `bar: true`, the `color: red; backgroundColor: yellow;` is applied when hover regardless of `foo` value, because the higher index of the array has higher specificity.

如果bar为真，则bar的css生效，因为更靠后的css有更高级的优先级，foo将被覆盖，也就和foo的值无关

> **Note**: Each index can be an `object` or `callback` 数组中的元素可以是对象，或者函数返回值

```
<Box
  sx={[
    { mr: 2, color: 'red' },
    (theme) => ({
      '&:hover': {
        color: theme.palette.primary.main,
      },
    }),
  ]}
/>
```

## Passing `sx` prop

sx参数的传递

If you want to receive `sx` prop from your component and pass it down to MUI's component, we recommend this approach:

如果你想从你的组件接收sx参数并传递到MUI‘s的组件，我们推荐如下做法



{{"demo": "PassingSxProp.js", "bg": true, "defaultCodeOpen": true}}



## TypeScript usage

ts的用法

A frequent source of confusion with the `sx` prop is TypeScript's [type widening](https://mariusschulz.com/blog/literal-type-widening-in-typescript), which causes this example not to work as expected:

一个频繁出现的令人困惑的问题是sx参数的ts类型扩展，它会导致如下问题

```
const style = {
  flexDirection: 'column',
};

export default function App() {
  return <Button sx={style}>Example</Button>;
}
//    Type '{ flexDirection: string; }' is not assignable to type 'SxProps<Theme> | undefined'.
//    Type '{ flexDirection: string; }' is not assignable to type 'CSSSelectorObject<Theme>'.
//      Property 'flexDirection' is incompatible with index signature.
//        Type 'string' is not assignable to type 'SystemStyleObject<Theme>'.
```



The problem is that the type of the `flexDirection` prop is inferred as `string`, which is too wide.

 这个问题是因为flexDirection参数的推论类型是string，它的类型范围太大了

To fix this, you can cast the object/function passed to the `sx` prop to const:

要固定它，你可以把传递给sx参数的对象或者函数用as const投射它的最小范围

```
const style = {
  flexDirection: 'column',
} as const;

export default function App() {
  return <Button sx={style}>Example</Button>;
}
```



Alternatively, you can pass the style object directly to the `sx` prop:

或者你可以这样直接将对象传递给sx

```
export default function App() {
  return <Button sx={{ flexDirection: 'column' }}>Example</Button>;
}
```

### `fill` callback gives theme type as `any`

填入函数返回值

Since `sx` can be an array type, there is a conflict in type of `Array.fill` and CSS's `fill` property when define value as a callback.

 当使用函数返回值作为参数，且sx是数组类型时，数组的自带fill方法和 css的fill属性就出现了一个冲突？？？

As a workaround, you can explicitly define the theme like this:

------

作为一个替代方案，你可以这样明确地定义Theme

```
import { Theme } from '@mui/material/styles';

<Box
  sx={{
    fill: (theme: Theme) => theme.palette.primary.main,
  }}
/>;
```

> Let us know or [submit a PR](https://github.com/mui/material-ui/pulls) if you have a proper way to fix this issue.
>
>  如果你有一个好方法来解决这个问题，请让我们知道，或者提交一个推动请求
>
> 🙏

## Performance

性能

If you are interested in the performance tradeoff, you can find more details [here](https://translate.mui.com/system/basics/#performance-tradeoff).

如果你对性能平衡感兴趣，可以在这里找到更多资料


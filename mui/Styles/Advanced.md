|                             原文                             |                             译文                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                      Advanced (LEGACY)                       |                         高级（遗留）                         |
| This section covers more advanced usage of @mui/styles.[![sketch](https://mui.com/static/ads-in-house/sketch.png)**For Sketch**. A large UI kit with over 600 handcrafted MUI symbols 💎.](https://mui.com/store/items/sketch-react/?utm_source=docs&utm_medium=referral&utm_campaign=in-house-sketch)ad by MUI |                                                              |
| ⚠️ `@mui/styles` is the ***legacy*** styling solution for MUI. It depends on [JSS](https://cssinjs.org/) as a styling solution, which is not used in the `@mui/material` anymore, deprecated in v5. If you don't want to have both emotion & JSS in your bundle, please refer to the [`@mui/system`](https://mui.com/system/basics/) documentation which is the recommended alternative. |                                                              |
| ⚠️ `@mui/styles` is not compatible with [React.StrictMode](https://reactjs.org/docs/strict-mode.html) or React 18. |                                                              |
|                           Theming                            |                             主题                             |
| Add a `ThemeProvider` to the top level of your app to pass a theme down the React component tree. Then, you can access the theme object in style functions. | 增加一个ThemeProvider 在你app 的最外层可以传递一个主题到react组件树。然后，你可以从样式函数中访问主题对象 |
| This example creates a theme object for custom-built components. If you intend to use some of the MUI's components you need to provide a richer theme structure using the `createTheme()` method. Head to the [theming section](https://mui.com/customization/theming/) to learn how to build your custom MUI theme. | 这个例子是给自定义组件创造一个主题对象。如果你打算使用MUI的一些组件，你需要通过使用createTheme方法提供一个丰富的主题。跳转到主题章节学习怎么建立自定义的MUI主题 |
| import { ThemeProvider } from '@mui/styles'; import DeepChild from './my_components/DeepChild';  const theme = {   background: 'linear-gradient(45deg, #FE6B8B 30%, #FF8E53 90%)', };  function Theming() {   return (     <ThemeProvider theme={theme}>       <DeepChild />     </ThemeProvider>   ); } |                                                              |
|                           Theming                            |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
| <ThemeProvider theme={themeInstance}>   <DeepChild /> </ThemeProvider> |                                                              |
|              Accessing the theme in a component              |                       在组件中访问主题                       |
| You might need to access the theme variables inside your React components. |           你可能需要动态访问主题在你的react组件中            |
|                       `useTheme` hook                        |                        useTheme hook                         |
|               For use in function components:                |                         用于函数组件                         |
| import { useTheme } from '@mui/styles';  function DeepChild() {   const theme = useTheme();   return <span>{`spacing ${theme.spacing}`}</span>; } |                                                              |
|                         spacing 8px                          |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
| <ThemeProvider<MyTheme>   theme={{     spacing: '8px',   }} >   <DeepChild /> </ThemeProvider> |                                                              |
|                       `withTheme` HOC                        |                      withTheme 高阶组件                      |
|           For use in class or function components:           |                      适用于类和函数组件                      |
| import { withTheme } from '@mui/styles';  function DeepChildRaw(props) {   return <span>{`spacing ${props.theme.spacing}`}</span>; }  const DeepChild = withTheme(DeepChildRaw); |                                                              |
|                         spacing 8px                          |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                        Theme nesting                         |                           主题嵌套                           |
| You can nest multiple theme providers. This can be really useful when dealing with different areas of your application that have distinct appearance from each other. | 你可以使用多个主题提供者相互嵌套。你的引用有不同区域要展现不同的效果时，者将会是有用的。 |
| <ThemeProvider theme={outerTheme}>   <Child1 />   <ThemeProvider theme={innerTheme}>     <Child2 />   </ThemeProvider> </ThemeProvider> |                                                              |
|                                                              |                                                              |
|                        Theme nesting                         |                                                              |
|                        Theme nesting                         |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
| The inner theme will **override** the outer theme. You can extend the outer theme by providing a function: |    内部主题将覆盖外部主题，你可以扩大外部主题通过这个函数    |
| <ThemeProvider theme={…} >   <Child1 />   <ThemeProvider theme={outerTheme => ({ darkMode: true, ...outerTheme })}>     <Child2 />   </ThemeProvider> </ThemeProvider> |                                                              |
|              Overriding styles - `classes` prop              |                           覆盖样式                           |
| The `makeStyles` (hook generator) and `withStyles` (HOC) APIs allow the creation of multiple style rules per style sheet. Each style rule has its own class name. The class names are provided to the component with the `classes` variable. This is particularly useful when styling nested elements in a component. | makeStyles（钩子生产器）和withStyles（高阶组件）api允许在每个样式表中创建多个样式。每一个样式有它自己的类名。类名可以通过classes变量提供给组件。这在组件使用样式嵌套时是非常有用的 |
| // A style sheet const useStyles = makeStyles({   root: {}, // a style rule   label: {}, // a nested style rule });  function Nested(props) {   const classes = useStyles();   return (     <button className={classes.root}>       {/* 'jss1' */}       <span className={classes.label}>{/* 'jss2' nested */}</span>     </button>   ); }  function Parent() {   return <Nested />; } |                                                              |
| However, the class names are often non-deterministic. How can a parent component override the style of a nested element? |    然而，类名是经常不确定的。父组件如何重写嵌套元素的样式    |
|                         `withStyles`                         |                                                              |
| This is the simplest case. The wrapped component accepts a `classes` prop, it simply merges the class names provided with the style sheet. | 这是个简单的例子，被包装的组件接受一个classes的参数，它只是合并样式表提供的类名 |
| const Nested = withStyles({   root: {}, // a style rule   label: {}, // a nested style rule })(({ classes }) => (   <button className={classes.root}>     <span className={classes.label}>{/* 'jss2 my-label' Nested*/}</span>   </button> ));  function Parent() {   return <Nested classes={{ label: 'my-label' }} />; } |                                                              |
|                         `makeStyles`                         |                                                              |
| The hook API requires a bit more work. You have to forward the parent props to the hook as a first argument. | 钩子api要多一点点工作，你必须将父元素传递过来的参数作为钩子函数的第一个参数 |
| const useStyles = makeStyles({   root: {}, // a style rule   label: {}, // a nested style rule });  function Nested(props) {   const classes = useStyles(props);   return (     <button className={classes.root}>       <span className={classes.label}>{/* 'jss2 my-label' nested */}</span>     </button>   ); }  function Parent() {   return <Nested classes={{ label: 'my-label' }} />; } |                                                              |
|                         JSS plugins                          |                                                              |
| JSS uses plugins to extend its core, allowing you to cherry-pick the features you need, and only pay the performance overhead for what you are using. | JSS使用插件扩展它的核心，允许你优先挑选你需要的功能，仅付出你使用组件的性能开销 |
| Not all the plugins are available in MUI by default. The following (which is a subset of [jss-preset-default](https://cssinjs.org/jss-preset-default/)) are included: |  并不是所有的插件在MUI是默认可用的。下面这些包括是可用的：   |
| [jss-plugin-rule-value-function](https://cssinjs.org/jss-plugin-rule-value-function/) [jss-plugin-global](https://cssinjs.org/jss-plugin-global/) [jss-plugin-nested](https://cssinjs.org/jss-plugin-nested/) [jss-plugin-camel-case](https://cssinjs.org/jss-plugin-camel-case/) [jss-plugin-default-unit](https://cssinjs.org/jss-plugin-default-unit/) [jss-plugin-vendor-prefixer](https://cssinjs.org/jss-plugin-vendor-prefixer/) [jss-plugin-props-sort](https://cssinjs.org/jss-plugin-props-sort/) |                                                              |
| Of course, you are free to use additional plugins. Here is an example with the [jss-rtl](https://github.com/alitaheri/jss-rtl) plugin. |      当然， 你可以自由增加插件，这是一个增加插件的样例       |
| import { create } from 'jss'; import { StylesProvider, jssPreset } from '@mui/styles'; import rtl from 'jss-rtl';  const jss = create({   plugins: [...jssPreset().plugins, rtl()], });  export default function App() {   return <StylesProvider jss={jss}>...</StylesProvider>; } |                                                              |
|                       String templates                       |                          字符串模板                          |
| If you prefer CSS syntax over JSS, you can use the [jss-plugin-template](https://cssinjs.org/jss-plugin-template/) plugin. | 如果你喜欢css语法超过jss，你可以使用jss-plugin-template插件  |
| const useStyles = makeStyles({   root: `     background: linear-gradient(45deg, #fe6b8b 30%, #ff8e53 90%);     border-radius: 3px;     font-size: 16px;     border: 0;     color: white;     height: 48px;     padding: 0 30px;     box-shadow: 0 3px 5px 2px rgba(255, 105, 135, 0.3);   `, }); |                                                              |
|  Note that this doesn't support selectors, or nested rules.  |             注意，这并不支持选择器，或者嵌套功能             |
|                       String templates                       |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                     CSS injection order                      |                         css注入顺序                          |
| It's **really important** to understand how the CSS specificity is calculated by the browser, as it's one of the key elements to know when overriding styles. You are encouraged to read this MDN paragraph: [How is specificity calculated?](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#How_is_specificity_calculated) | 理解浏览器是怎么计算css特性是非常重要的。这是掌握重写样式的关键要素之一，鼓励你去读一下如何计算特异性 |
| By default, the style tags are injected **last** in the `<head>` element of the page. They gain more specificity than any other style tags on your page e.g. CSS modules, styled components. | 默认情况下，样式标签是最后注入页面的head元素的，比起页面css模块的其他样式标签他们将获得更高的优先级 |
|                         injectFirst                          |                                                              |
| The `StylesProvider` component has an `injectFirst` prop to inject the style tags **first** in the head (less priority): | StylesProvider组件有一个injectFirst参数可以让样式标签第一个注入head |
| import { StylesProvider } from '@mui/styles';  <StylesProvider injectFirst>   {/* Your component tree.       Styled components can override MUI's styles. */} </StylesProvider>; |                                                              |
|            `makeStyles` / `withStyles` / `styled`            |                                                              |
| The injection of style tags happens in the **same order** as the `makeStyles` / `withStyles` / `styled` invocations. For instance the color red wins in this case: | makeStyles/withStyles/styled装置的样式标签注入顺序是相同的。下面的例子中，红色获胜 |
| import clsx from 'clsx'; import { makeStyles } from '@mui/styles';  const useStylesBase = makeStyles({   root: {     color: 'blue', // 🔵   }, });  const useStyles = makeStyles({   root: {     color: 'red', // 🔴   }, });  export default function MyComponent() {   // Order doesn't matter   const classes = useStyles();   const classesBase = useStylesBase();    // Order doesn't matter   const className = clsx(classes.root, classesBase.root);    // color: red 🔴 wins.   return <div className={className} />; } |                                                              |
| The hook call order and the class name concatenation order **don't matter**. |           钩子的调用顺序和类名顺序是不影响优先级的           |
|                        insertionPoint                        |                            插入点                            |
| JSS [provides a mechanism](https://github.com/cssinjs/jss/blob/master/docs/setup.md#specify-the-dom-insertion-point) to control this situation. By adding an `insertionPoint` within the HTML you can [control the order](https://cssinjs.org/jss-api/#attach-style-sheets-in-a-specific-order) that the CSS rules are applied to your components. | JSS提供一个装置来控制这种情况。通过在html中增加一个插入点，你可以控制css规则在你组件中的应用 |
|                         HTML comment                         |                             要素                             |
| The simplest approach is to add an HTML comment to the `<head>` that determines where JSS will inject the styles: | 最简单的方式是在head的jss将插入样式的地方增加一个html注释。  |
| <head>   <!-- jss-insertion-point -->   <link href="..." /> </head> import { create } from 'jss'; import { StylesProvider, jssPreset } from '@mui/styles';  const jss = create({   ...jssPreset(),   // Define a custom insertion point that JSS will look for when injecting the styles into the DOM.   insertionPoint: 'jss-insertion-point', });  export default function App() {   return <StylesProvider jss={jss}>...</StylesProvider>; } |                                                              |
|                     Other HTML elements                      |                         其他html元素                         |
| [Create React App](https://github.com/facebook/create-react-app) strips HTML comments when creating the production build. To get around this issue, you can provide a DOM element (other than a comment) as the JSS insertion point, for example, a `<noscript>` element: | create react app 创建生产包的时候会拆分html注释。为了避开这个问题，你可以提供一个DOM元素而不是一个评论作为jss的插入点，比如，一个noscript元素 |
| <head>   <noscript id="jss-insertion-point" />   <link href="..." /> </head> import { create } from 'jss'; import { StylesProvider, jssPreset } from '@mui/styles';  const jss = create({   ...jssPreset(),   // Define a custom insertion point that JSS will look for when injecting the styles into the DOM.   insertionPoint: document.getElementById('jss-insertion-point'), });  export default function App() {   return <StylesProvider jss={jss}>...</StylesProvider>; } |                                                              |
|                       JS createComment                       |                          js创建评论                          |
| codesandbox.io prevents access to the `<head>` element. To get around this issue, you can use the JavaScript `document.createComment()` API: | 沙盒箱子的io阻止获取head元素，为了避开这个问题，你可以使用js的document.createComment()api |
| import { create } from 'jss'; import { StylesProvider, jssPreset } from '@mui/styles';  const styleNode = document.createComment('jss-insertion-point'); document.head.insertBefore(styleNode, document.head.firstChild);  const jss = create({   ...jssPreset(),   // Define a custom insertion point that JSS will look for when injecting the styles into the DOM.   insertionPoint: 'jss-insertion-point', });  export default function App() {   return <StylesProvider jss={jss}>...</StylesProvider>; } |                                                              |
|                    Server-side rendering                     |                         服务器端渲染                         |
| This example returns a string of HTML and inlines the critical CSS required, right before it's used: | 这个例子返回一个html的字符串和极重要的css，就在它被使用之前  |
| import ReactDOMServer from 'react-dom/server'; import { ServerStyleSheets } from '@mui/styles';  function render() {   const sheets = new ServerStyleSheets();    const html = ReactDOMServer.renderToString(sheets.collect(<App />));   const css = sheets.toString();    return ` <!DOCTYPE html> <html>   <head>     <style id="jss-server-side">${css}</style>   </head>   <body>     <div id="root">${html}</div>   </body> </html>   `; } |                                                              |
| You can [follow the server side guide](https://mui.com/guides/server-rendering/) for a more detailed example, or read the [`ServerStyleSheets` API documentation](https://mui.com/styles/api/#serverstylesheets). | 你可以跟随服务端指南来获得一个更详细的案例，或者读服务端样式轮子的文档 |
|                            Gatsby                            |                            盖茨比                            |
| There is [an official Gatsby plugin](https://github.com/hupe1980/gatsby-plugin-material-ui) that enables server-side rendering for `@mui/styles`. Refer to the plugin's page for setup and usage instructions. | 这是一个官方的盖茨比插件。它可以后端渲染@mui/styles。安装和使用说明请参考插件页面 |
| Refer to [this example Gatsby project](https://github.com/mui/material-ui/tree/master/examples/gatsby) for an up-to-date usage example. |            参考盖茨比项目案例来获得最新的使用案例            |
|                           Next.js                            |                                                              |
| You need to have a custom `pages/_document.js`, then copy [this logic](https://github.com/mui/material-ui/blob/814fb60bbd8e500517b2307b6a297a638838ca89/examples/nextjs/pages/_document.js#L52-L59) to inject the server-side rendered styles into the `<head>` element. | 你需要有一个自定义的页面，或者文档，复制这个逻辑给head元素插入服务端渲染样式 |
| Refer to [this example project](https://github.com/mui/material-ui/tree/master/examples/nextjs) for an up-to-date usage example. |               参考这个项目案例获得最新使用例子               |
|                         Class names                          |                             类名                             |
| The class names are generated by [the class name generator](https://mui.com/styles/api/#creategenerateclassname-options-class-name-generator). |                    类名是由类名生成器生成                    |
|                           Default                            |                                                              |
| By default, the class names generated by `@mui/styles` are **non-deterministic**; you can't rely on them to stay the same. Let's take the following style as an example: | 默认情况下，被@mui/styles生产的类名是不确定的。你不能相信他们一直保持一样，让我们以项目的样式为例 |
| const useStyles = makeStyles({   root: {     opacity: 1,   }, }); |                                                              |
| This will generate a class name such as `makeStyles-root-123`. |           这个将生成一个makeStyles-root-123的类名            |
| You have to use the `classes` prop of a component to override the styles. The non-deterministic nature of the class names enables style isolation. | 你必须使用classes参数来重写样式，不确定的自然属性使样式自然产生隔离 |
| In **development**, the class name is: `.makeStyles-root-123`, following this logic: |      在开发环境中，类名.makeStyles-root-123遵循这个逻辑      |
| const sheetName = 'makeStyles'; const ruleName = 'root'; const identifier = 123;  const className = `${sheetName}-${ruleName}-${identifier}`; |                                                              |
| In **production**, the class name is: `.jss123`, following this logic: |          在工作环境中，类名是.jss123,遵循这个逻辑：          |
| const productionPrefix = 'jss'; const identifier = 123;  const className = `${productionPrefix}-${identifier}`; |                                                              |
| However, when the following conditions are met, the class names are **deterministic**: |              然而，满足下面条件时，类名是确定的              |
| Only one theme provider is used (**No theme nesting**) The style sheet has a name that starts with `Mui` (all MUI components). The `disableGlobal` option of the [class name generator](https://mui.com/styles/api/#creategenerateclassname-options-class-name-generator) is `false` (the default). | 只有一个主题，没有主题嵌套；样式表以Mui作为开头名（所有组件都是MUI组件）；类名生成器的禁用全局属性是false（默认） |
|                          Global CSS                          |                           全局css                            |
|                     `jss-plugin-global`                      |                                                              |
| The [`jss-plugin-global`](https://mui.com/styles/advanced/#jss-plugins) plugin is installed in the default preset. You can use it to define global class names. | jss-plugin-global插件默认是安装的；你可以使用它来定义全局类名 |
|                                                              |                                                              |
|                                                              |                                                              |
|       <div className="cssjss-advanced-global-child" />       |                                                              |
|                            Hybrid                            |                                                              |
| You can also combine JSS generated class names with global ones. |              你可以混合全局类名和jss生成的类名               |
|                                                              |                                                              |
|                                                              |                                                              |
|                  <div className="child" />                   |                                                              |
|                         CSS prefixes                         |                           css 前缀                           |
| JSS uses feature detection to apply the correct prefixes. [Don't be surprised](https://github.com/mui/material-ui/issues/9293) if you can't see a specific prefix in the latest version of Chrome. Your browser probably doesn't need it. | jss使用特征检测来获取正确的前缀。如果你不能发现明确的前缀在最新的Chrome浏览器中不要惊奇，你的浏览器大概不需要它 |
|                       TypeScript usage                       |                                                              |
| Using `withStyles` in TypeScript can be a little tricky, but there are some utilities to make the experience as painless as possible. | 在ts中使用withStyles有一点棘手，但这里有很多工具可以让这个过程无痛。 |
|         Using `createStyles` to defeat type widening         |                使用createStyles来防止类型扩散                |
| A frequent source of confusion is TypeScript's [type widening](https://mariusschulz.com/blog/literal-type-widening-in-typescript), which causes this example not to work as expected: | 一个常见的困惑就是ts类型扩散，它经常照成下面这个例子不按预期工作 |
| const styles = {   root: {     display: 'flex',     flexDirection: 'column',   }, };  withStyles(styles); //         ^^^^^^ //         Types of property 'flexDirection' are incompatible. //           Type 'string' is not assignable to type '"-moz-initial" \| "inherit" \| "initial" \| "revert" \| "unset" \| "column" \| "column-reverse" \| "row"...'. |                                                              |
| The problem is that the type of the `flexDirection` prop is inferred as `string`, which is too wide. To fix this, you can pass the styles object directly to `withStyles`: | FlexDirection参数的类型被推论为字符串，这太宽了。要解决此问题，你可以直接传递样式对象给withStyles |
| withStyles({   root: {     display: 'flex',     flexDirection: 'column',   }, }); |                                                              |
| However type widening rears its ugly head once more if you try to make the styles depend on the theme: | 尽管类型扩展一次又一次抬起它难看的头，如果你想让样式依赖于主题 |
| withStyles(({ palette, spacing }) => ({   root: {     display: 'flex',     flexDirection: 'column',     padding: spacing.unit,     backgroundColor: palette.background.default,     color: palette.primary.main,   }, })); |                                                              |
| This is because TypeScript [widens the return types of function expressions](https://github.com/Microsoft/TypeScript/issues/241). |                  这是因为ts扩展了返回值类型                  |
| Because of this, using the `createStyles` helper function to construct your style rules object is recommended: | 就因为如此，使用createStyles将帮助函数构造样式对象是值得推荐的 |
| // Non-dependent styles const styles = createStyles({   root: {     display: 'flex',     flexDirection: 'column',   }, });  // Theme-dependent styles const styles = ({ palette, spacing }: Theme) =>   createStyles({     root: {       display: 'flex',       flexDirection: 'column',       padding: spacing.unit,       backgroundColor: palette.background.default,       color: palette.primary.main,     },   }); |                                                              |
| `createStyles` is just the identity function; it doesn't "do anything" at runtime, just helps guide type inference at compile time. | createStyles只是恒等函数，它在运行时不做任何事情，除了在编译时帮助推断类型 |
|                        Media queries                         |                           媒体查询                           |
| `withStyles` allows a styles object with top level media-queries like so: |         withStyles允许样式对象像这样使用顶级媒体查询         |
| const styles = createStyles({   root: {     minHeight: '100vh',   },   '@media (min-width: 960px)': {     root: {       display: 'flex',     },   }, }); |                                                              |
| To allow these styles to pass TypeScript however, the definitions have to be unambiguous concerning the names for CSS classes and actual CSS property names. Due to this, class names that are equal to CSS properties should be avoided. | 然而，允许这些样式传入ts，css类名和css真实属性名必须有明确的定义，所以，类名和css属性名要避免相同。 |
| // error because TypeScript thinks `@media (min-width: 960px)` is a class name // and `content` is the CSS property const ambiguousStyles = createStyles({   content: {     minHeight: '100vh',   },   '@media (min-width: 960px)': {     content: {       display: 'flex',     },   }, });  // works just fine const ambiguousStyles = createStyles({   contentClass: {     minHeight: '100vh',   },   '@media (min-width: 960px)': {     contentClass: {       display: 'flex',     },   }, }); |                                                              |
|           Augmenting your props using `WithStyles`           |                      使用ws增加你的参数                      |
| Since a component decorated with `withStyles(styles)` gets a special `classes` prop injected, you will want to define its props accordingly: | 当使用ws装饰组件时会获得一个特殊的classes参数注入，你需要照着定义它的参数 |
| const styles = (theme: Theme) =>   createStyles({     root: {       /* ... */     },     paper: {       /* ... */     },     button: {       /* ... */     },   });  interface Props {   // non-style props   foo: number;   bar: boolean;   // injected style props   classes: {     root: string;     paper: string;     button: string;   }; } |                                                              |
| However this isn't very [DRY](https://en.wikipedia.org/wiki/Don't_repeat_yourself) because it requires you to maintain the class names (`'root'`, `'paper'`, `'button'`, ...) in two different places. We provide a type operator `WithStyles` to help with this, so that you can just write: | 然呢，这并不是非常冗余，因为它要求你在两个不同的地方维护类名，我们提供了一个类型操作ws来帮助做这个事，你可以这样写 |
| import { createStyles, WithStyles } from '@mui/styles';  const styles = (theme: Theme) =>   createStyles({     root: {       /* ... */     },     paper: {       /* ... */     },     button: {       /* ... */     },   });  interface Props extends WithStyles<typeof styles> {   foo: number;   bar: boolean; } |                                                              |
|                    Decorating components                     |                           装饰组件                           |
| Applying `withStyles(styles)` as a function works as expected: |            应用ws（styles）作为一个函数按预期工作            |
| const DecoratedSFC = withStyles(styles)(({ text, type, color, classes }: Props) => (   <Typography variant={type} color={color} classes={classes}>     {text}   </Typography> ));  const DecoratedClass = withStyles(styles)(   class extends React.Component<Props> {     render() {       const { text, type, color, classes } = this.props;       return (         <Typography variant={type} color={color} classes={classes}>           {text}         </Typography>       );     }   }, ); |                                                              |
| Unfortunately due to a [current limitation of TypeScript decorators](https://github.com/Microsoft/TypeScript/issues/4881), `withStyles(styles)` can't be used as a decorator in TypeScript. | 不幸的事，由于ts装饰器目前的限制，ws不能作为一个装饰器在ts中使用 |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |


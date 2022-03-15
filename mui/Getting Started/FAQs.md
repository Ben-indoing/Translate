|                             原文                             |                             译文                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                  Frequently Asked Questions                  |                      频繁地被问到的问题                      |
| Stuck on a particular problem? Check some of these common gotchas first in the FAQ.[![templates](https://mui.com/static/ads-in-house/themes-2.jpg)**Premium Templates**. Start your project with the best templates for admins, dashboards, and more.](https://mui.com/store/?utm_source=docs&utm_medium=referral&utm_campaign=in-house-templates)ad by MUI |  被困在一个特定的问题上了吗？首先在FAQ里检查一些常见的问题   |
| If you still can't find what you're looking for, you can refer to our [support page](https://mui.com/getting-started/support/). |    如果你仍然没找到你所需要的，你可以参考到我们的支持页面    |
|        MUI is awesome. How can I support the project?        |           Mui是令人惊叹的，我怎么才能支持这个项目            |
|             There are many ways to support MUI:              |                    有许多方式可以支持MUI                     |
| **Spread the word**. Evangelize MUI by [linking to mui.com](https://mui.com/) on your website, every backlink matters. Follow us on [Twitter](https://twitter.com/MUI_hq), like and retweet the important news. Or just talk about us with your friends. **Give us feedback**. Tell us what we're doing well or where we can improve. Please upvote (👍) the issues that you are the most interested in seeing solved. **Help new users**. You can answer questions on [StackOverflow](https://stackoverflow.com/questions/tagged/mui). Make changes happen.  Edit the documentation. Every page has an "EDIT THIS PAGE" link in the top right. Report bugs or missing features by [creating an issue](https://github.com/mui/material-ui/issues/new). Review and comment on existing [pull requests](https://github.com/mui/material-ui/pulls) and [issues](https://github.com/mui/material-ui/issues). Help [translate](https://translate.mui.com/) the documentation. [Improve our documentation](https://github.com/mui/material-ui/tree/HEAD/docs), fix bugs, or add features by [submitting a pull request](https://github.com/mui/material-ui/pulls). **Support us financially on [OpenCollective](https://opencollective.com/mui)**. If you use MUI in a commercial project and would like to support its continued development by becoming a Sponsor, or in a side or hobby project and would like to become a Backer, you can do so through OpenCollective. All funds donated are managed transparently, and Sponsors receive recognition in the README and on the MUI home page. | 告诉他人，通过这个链接传播MUI在你的网站上。关注我们Twitter，点赞并转发我们的重要消息。或者和你的朋友聊聊我们。给与我们反馈。告诉我们哪里做得好或者哪里需要改进。请点赞你最关心的被解决的问题。帮助新手。你可以在stackOverFlow上回答问题。让这些改变发生。编辑文档。每一个页面的右上角有一个“编辑这个页面”的链接。通过创造新的议题，报告bugs或者缺失的功能。审查或者评论存在的pull requests 和议题。帮助翻译文档，或者改善文档。修复bugs，或者通过提交pull request来增加功能。通过Opencollective来在财政上支持我们。如果你在商业项目中使用MUI，或者想变成一个赞助者来支持它持续成长，或者业余爱好项目想成为支持者，你可以通过OpenCollective来实现。所有捐赠的自己都是透明管理的，赞助商会在README文档和MUI的首页被记录 |
| Why do the fixed positioned elements move when a modal is opened? |         为什么固定位置的元素在打开一个modal时会移动          |
| Scrolling is blocked as soon as a modal is opened. This prevents interacting with the background when the modal should be the only interactive content. However, removing the scrollbar can make your **fixed positioned elements** move. In this situation, you can apply a global `.mui-fixed` class name to tell MUI to handle those elements. | 当一个模块被打开时，滚动条将会被阻断。这防止与背景的交互，被打开的模块将是当前唯一交互的内容。然而，移除滚动条会使你的固定位置的元素移动。在这个情况下，你可以应用一个全局类.mui-fixed来告诉MUI处理这些元素 |
|        How can I disable the ripple effect globally?         |                如何全局禁用ripple（涟漪）效果                |
| The ripple effect is exclusively coming from the `BaseButton` component. You can disable the ripple effect globally by providing the following in your theme: | 涟漪效果唯一来自BaseButton组件，你可以全局禁止涟漪效果通过提供下面的主题： |
| import { createTheme } from '@mui/material';  const theme = createTheme({   components: {     // Name of the component ⚛️     MuiButtonBase: {       defaultProps: {         // The props to apply         disableRipple: true, // No more ripple, on the whole application 💣!       },     },   }, }); |                                                              |
|           How can I disable transitions globally?            |                    我如何禁用全局转换效果                    |
| MUI uses the same theme helper for creating all its transitions. Therefore you can disable all transitions by overriding the helper in your theme: | MUI使用同样的主题助手来创造它的转换效果。因此，你可以通过重写theme来禁用转换效果 |
| import { createTheme } from '@mui/material';  const theme = createTheme({   transitions: {     // So we have `transition: none;` everywhere     create: () => 'none',   }, }); |                                                              |
| It can be useful to disable transitions during visual testing or to improve performance on low-end devices. |  禁止转换效果对视觉测试或者在低端设备上改善性能是非常有效的  |
| You can go one step further by disabling all transitions and animations effects: |        你可以更进一步地禁止所有的转换你效果和动画效果        |
| import { createTheme } from '@mui/material';  const theme = createTheme({   components: {     // Name of the component ⚛️     MuiCssBaseline: {       styleOverrides: {         '*, *::before, *::after': {           transition: 'none !important',           animation: 'none !important',         },       },     },   }, }); |                                                              |
| Notice that the usage of `CssBaseline` is required for the above approach to work. If you choose not to use it, you can still disable transitions and animations by including these CSS rules: | 注意cssBaseLine的用法是要求对于上述方法生效。如果你没有选择使用它，你仍然可以通过加入下面的css规则来禁用转换和动画 |
| *, *::before, *::after {   transition: 'none !important';   animation: 'none !important'; } |                                                              |
|          Do I have to use emotion to style my app?           |            我必须使用emotion来控制我app的样式吗？            |
| No, it's not required. But if you are using the default styled engine (`@mui/styled-engine`) the emotion dependency comes built in, so carries no additional bundle size overhead. | 不，它不是必须的；但如果你使用默认样式引擎，emotion依赖默认安装；所以没有传递额外的打包大小开销。 |
| Perhaps, however, you're adding some MUI components to an app that already uses another styling solution, or are already familiar with a different API, and don't want to learn a new one? In that case, head over to the [Style Library Interoperability](https://mui.com/guides/interoperability/) section, where we show how simple it is to restyle MUI components with alternative style libraries. | 可能，然而，你可以给一个应用增加一些MUI组件，这些组件已经使用了另外的样式解决方案，或者已经熟悉不同的api，不想再学习一个新的。在这种情况下，前往互用性样式库章节。那里我们将给你展示怎么简单地改变MUI组件的样式通过其他的样式库 |
|           When should I use inline-style vs. CSS?            |               什么时候我可以使用内联样式css？                |
| As a rule of thumb, only use inline-styles for dynamic style properties. The CSS alternative provides more advantages, such as: | 一般来说，仅对动态样式属性使用内联css。css替代物具有很多优点，比如 |
|   auto-prefixing better debugging media queries keyframes    |           自动前缀， 更好的调试，媒体查询，关键帧            |
|                  How do I use react-router?                  |                     我怎么使用react路由                      |
| We detail the [integration with third-party routing libraries](https://mui.com/guides/routing/) like react-router, Gatsby or Next.js in our guide. | 我们详细地融入了第三方的路由库，像react-router，Gatsby 或者Next.js在我们的指南中 |
|              How can I access the DOM element?               |                     我该怎么获得DOM元素                      |
| All MUI components that should render something in the DOM forward their ref to the underlying DOM component. This means that you can get DOM elements by reading the ref attached to MUI components: | 所有的MUI组件在DOM中渲染东西时转发他们的ref将植入DOM组件，这意味着你可以通过读取隶属于MUI组件的ref来获得DOM元素 |
| // or a ref setter function const ref = React.createRef(); // render <Button ref={ref} />; // usage const element = ref.current; |                                                              |
| If you're not sure if the MUI component in question forwards its ref you can check the API documentation under "Props" e.g. the [Button API](https://mui.com/api/button/#props) includes | 如果你不确信，MUI组件转发它的是否有问题，你可以检查Props的API文档，例如Button API文档中包括 |
|          The ref is forwarded to the root element.           |                       ref传递给根元素                        |
|  indicating that you can access the DOM element with a ref.  |                  表面你可以通过ref来链接DOM                  |
|        I have several instances of styles on the page        |                  我有若干个样式实例在页面上                  |
| If you are seeing a warning message in the console like the one below, you probably have several instances of `@mui/styles` initialized on the page. | 如果你看见一个如下的警告在控制台，你可能拥有若干个实例在页面上初始化 |
| It looks like there are several instances of `@mui/styles` initialized in this application. This may cause theme propagation issues, broken class names, specificity issues, and make your application bigger without a good reason. | 看起来有多个@mui/styles实例在应用中初始化。这会导致主题传播问题，破坏类名，特异性问题，和让你的应用无故增大 |
|                       Possible reasons                       |                          可能的原因                          |
|     There are several common reasons for this to happen:     |                这里有若干个理由会导致它的发生                |
| You have another `@mui/styles` library somewhere in your dependencies. You have a monorepo structure for your project (e.g, lerna, yarn workspaces) and `@mui/styles` module is a dependency in more than one package (this one is more or less the same as the previous one). You have several applications that are using `@mui/styles` running on the same page (e.g., several entry points in webpack are loaded on the same page). | 你拥有另一个@mui/styles库在你所依赖的某个地方。你有使用一个存储库结构的项目，然后@mui/styles 模块被超过一个项目所依赖（这个项目和前一个差不多）。你有若干个应用，使用@mui/styles运行在同一个页面。例如若干个webpack的入口被加载在同一个页面 |
|              Duplicated module in node_modules               |                   node_modules中的重复模块                   |
| If you think that the issue may be in the duplication of the @mui/styles module somewhere in your dependencies, there are several ways to check this. You can use `npm ls @mui/styles`, `yarn list @mui/styles` or `find -L ./node_modules | grep /@mui/styles/package.json` commands in your application folder. | 如果你认为可能有问题再你依赖的某个地方复制复制了@mui/styles模块，这里有若干不同的方法来检查。你可以在你的文件夹里使用.....等命令 |
| If none of these commands identified the duplication, try analyzing your bundle for multiple instances of @mui/styles. You can just check your bundle source, or use a tool like [source-map-explorer](https://github.com/danvk/source-map-explorer) or [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer). | 如果没有一种命令能识别重复模块，尝试分解你打包的多个@mui/styles实例，你可以检查你打包的资源，或者使用这两种工具 |
| If you identified that duplication is the issue that you are encountering there are several things you can try to solve it: | 如果你发现重复模块是你所遇到的问题，这里有几种方式你可以尝试去解决它 |
| If you are using npm you can try running `npm dedupe`. This command searches the local dependencies and tries to simplify the structure by moving common dependencies further up the tree. | 如果你使用npm，你可以尝试运行npm dedupe。这个命令搜索本地的依赖并尝试通过把共同的依赖往上移动来简化结构 |
| If you are using webpack, you can change the way it will [resolve](https://webpack.js.org/configuration/resolve/#resolve-modules) the @mui/styles module. You can overwrite the default order in which webpack will look for your dependencies and make your application node_modules more prioritized than default node module resolution order: | 如果你使用webpack，你可以改变方式，它将解决@mui/styles module。你可以重写默认顺序，webpack将寻找的你的依赖并使你的应用的mode_modules比默认的方法解析顺序更加有序 |
| resolve: { +   alias: { +     "@mui/styles": path.resolve(appFolder, "node_modules", "@mui/styles"), +   }   } |                                                              |
|                       Usage with Lerna                       |                         Lerna的用法                          |
| One possible fix to get @mui/styles to run in a Lerna monorepo across packages is to [hoist](https://github.com/lerna/lerna/blob/HEAD/doc/hoist.md) shared dependencies to the root of your monorepo file. Try running the bootstrap option with the --hoist flag. | 一种可能的解决方案@mui/styles 运行一个Lerna monorepo包管理结构是提升共享依赖在你的基础的monorepo文件。尝试运行bootstrap选项使用hoist flag命令 |
|                   lerna bootstrap --hoist                    |                                                              |
| Alternatively, you can remove @mui/styles from your package.json file and hoist it manually to your top-level package.json file. | 或者，你可以从你的package.json文件中移除@mui/styles，并手动提升它到你更高级的package.json文件中 |
|    Example of a package.json file in a Lerna root folder     |        这是一个Lerna根目录文件夹的package.json的例子         |
| {   "name": "my-monorepo",   "devDependencies": {     "lerna": "latest"   },   "dependencies": {     "@mui/styles": "^4.0.0"   },   "scripts": {     "bootstrap": "lerna bootstrap",     "clean": "lerna clean",     "start": "lerna run start",     "build": "lerna run build"   } } |                                                              |
|          Running multiple applications on one page           |                   运行多个应用在一个页面上                   |
| If you have several applications running on one page, consider using one @mui/styles module for all of them. If you are using webpack, you can use [CommonsChunkPlugin](https://webpack.js.org/plugins/commons-chunk-plugin/) to create an explicit [vendor chunk](https://webpack.js.org/plugins/commons-chunk-plugin/#explicit-vendor-chunk), that will contain the @mui/styles module: | 如果你有几个应用程序在一个页面上运行，考虑共用一个@mui/styles 模块 |
| module.exports = {     entry: { +     vendor: ["@mui/styles"],       app1: "./src/app.1.js",       app2: "./src/app.2.js",     },     plugins: [ +     new webpack.optimize.CommonsChunkPlugin({ +       name: "vendor", +       minChunks: Infinity, +     }),     ]   } |                                                              |
|        My App doesn't render correctly on the server         |               我的app没有在服务器上正确的渲染                |
| If it doesn't work, in 99% of cases it's a configuration issue. A missing property, a wrong call order, or a missing component – server-side rendering is strict about configuration. | 如果它不起作用，99%的可能，是它配置问题。一个缺失的属性，一个错误的呼叫顺序 |
| The best way to find out what's wrong is to compare your project to an **already working setup**. Check out the [reference implementations](https://mui.com/guides/server-rendering/#reference-implementations), bit by bit. |                     找出错误的最佳方法是                     |
| Why are the colors I am seeing different from what I see here? |                为什么我看到的颜色和这里不一样                |
| The documentation site is using a custom theme. Hence, the color palette is different from the default theme that MUI ships. Please refer to [this page](https://mui.com/customization/theming/) to learn about theme customization. | 文档使用的是自定义主题，因此颜色调色板是不同于MUI的默认主题的，请参考这个页面去学习怎么自定义主题 |
| Why does component X require a DOM node in a prop instead of a ref object? |      为什么组件X要求一个DOM节点作为一个参数替代ref对象       |
| Components like the [Portal](https://mui.com/api/portal/#props) or [Popper](https://mui.com/api/popper/#props) require a DOM node in the `container` or `anchorEl` prop respectively. It seems convenient to simply pass a ref object in those props and let MUI access the current value. This works in a simple scenario: | Portal 或者 Popper 这样的组件，需要在容器或者锚中分别传入一个DOM 节点。仅仅传一个ref对象在这些参数中，让MUI获得正确的值看起来很方便。这适用于一个简单的场景 |
| function App() {   const container = React.useRef(null);    return (     <div className="App">       <Portal container={container}>         <span>portaled children</span>       </Portal>       <div ref={container} />     </div>   ); } |                                                              |
| where `Portal` would only mount the children into the container when `container.current` is available. Here is a naive implementation of Portal: | Portal会在容器中挂载子元素，当容器的当前世可用时，这是portal的原生执行流程 |
| function Portal({ children, container }) {   const [node, setNode] = React.useState(null);    React.useEffect(() => {     setNode(container.current);   }, [container]);    if (node === null) {     return null;   }   return ReactDOM.createPortal(children, node); } |                                                              |
| With this simple heuristic `Portal` might re-render after it mounts because refs are up-to-date before any effects run. However, just because a ref is up-to-date doesn't mean it points to a defined instance. If the ref is attached to a ref forwarding component it is not clear when the DOM node will be available. In the example above, the `Portal` would run an effect once, but might not re-render because `ref.current` is still `null`. This is especially apparent for React.lazy components in Suspense. The above implementation could also not account for a change in the DOM node. | Portal会重新渲染，当它挂载子组件时，因为refs 是最新的在任何Effects运行之前，然而，ref最新并不意味着它指向一个实例。如果ref隶属于一个ref转发组件，它不清楚的当DOM节点是否可用。在上面的例子中，Portal会运行Effect一次，但没有重新渲染，因为ref.current仍然是null，这对React.lazy组件在悬链中式显而易见的。上述实现也不能解释DOM节点的变化。 |
| This is why we require a prop with the actual DOM node so that React can take care of determining when the `Portal` should re-render: | 这是我们要求一个实际DOM节点作为参数的原因，那样，react可以注意到Portal什么时候应该重新渲染 |
| function App() {   const [container, setContainer] = React.useState(null);   const handleRef = React.useCallback(     (instance) => setContainer(instance),     [setContainer],   );    return (     <div className="App">       <Portal container={container}>         <span>Portaled</span>       </Portal>       <div ref={handleRef} />     </div>   ); } |                                                              |
|               What's the clsx dependency for?                |                    clsx依赖是用来干嘛的？                    |
| [clsx](https://github.com/lukeed/clsx) is a tiny utility for constructing `className` strings conditionally, out of an object with keys being the class strings, and values being booleans. | clsx是一个微小的工具用于有条件的构造类名，在一个对象之外，键值变成类字符串，值变成布尔值。 |
|                     Instead of writing:                      |                                                              |
| // let disabled = false, selected = true;  return (   <div     className={`MuiButton-root ${disabled ? 'Mui-disabled' : ''} ${       selected ? 'Mui-selected' : ''     }`}   /> ); |                                                              |
|                         you can do:                          |                                                              |
| import clsx from 'clsx';  return (   <div     className={clsx('MuiButton-root', {       'Mui-disabled': disabled,       'Mui-selected': selected,     })}   /> ); |                                                              |
| I cannot use components as selectors in the styled() utility. What should I do? |    我不能使用组件作为选择器在styled（）工具，我该怎么办？    |
| If you are getting the error: `TypeError: Cannot convert a Symbol value to a string`, take a look at the [styled()](https://mui.com/system/styled/#how-to-use-components-selector-api) docs page for instructions on how you can fix this. | 如果你得到了这个错误：类型错误：不能把一个象征值转换成一个字符串，看一看styled的文档，看看怎么修复它 |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |


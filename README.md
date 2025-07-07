# Vue migration 

我正在设计一个 Vue 2 到 Vue 3 的规模化迁移方案，我需要你根据我的 task 编写迁移脚本。相关信息：

- vue-elment-admin 是原来的模板应用
- vue3-element-plus-admin 是新的工程模板（你要工作在这个工程中）
- migrate-cli 是未来我要编写的迁移脚本，将使用 gogocode 进行代码迁移，因此需要对齐原来的工程。

我的目标技术栈是： TypeScript/Javascript + vuex + vue router 4 + element-plus


Todos: 

1. 使用 Gogocode Vue 来转换 Vue 代码：https://github.com/thx/gogocode/tree/main/packages/gogocode-plugin-vue
2. SASS 迁移，结合 sass-migrator: https://sass-lang.com/documentation/breaking-changes/import/
3. Webpack 4 to 5: https://webpack.js.org/migrate/5/
4. 三方组件兼容层设计

```mermaid
flowchart TD
    A[Vue SFC File] --> B1[Parse Template Block]
    A --> B2[Parse Script Block]
    A --> B3[Parse Style Block]

    B1 --> T1[Template AST]
    T1 --> T2[Element Node: div]
    T2 --> T3[Attribute: class=msg]
    T2 --> T4[Interpolation: message]

    B2 --> S1[Script AST]
    S1 --> S2[Export Default Declaration]
    S2 --> S3[data method]
    S3 --> S4[Return: message Hello World]

    B3 --> C1[Style AST]
    C1 --> C2[Rule: .msg]
    C2 --> C3[Declaration: color = red]

    T1 --> M1[Generate Render Function]
    S1 --> M1
    M1 --> M2[Component Definition]

    C1 --> M3[Inject Scoped Style]
```

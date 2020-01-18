## node_modous
用来存放前端项目的所需模块，与`package,json`配合。

`package,json`规定在`install`时，放入`node_modous`的依赖项，包括其具体的版本等；`node_modous`用来存放`package,json`中规定的依赖项。
### `import`导入相关模块
1. `Importing default export`
```
  import GIVEN_NAME from ADDRESS
```
从`ADDRESS`导入默认的组件，并命名为`GIVEN_NAME`
2. `Importing named values`
```
  import { PARA_NAME } from ADDRESS
```
从`ADDRESS`导入`PARA_NAME`组件
3. `Importing a combination of Default Exports and Named Values`
```
  import GIVEN_NAME, { PARA_NAME, ... } from ADDRESS
```
从`ADDRESS`导入默认组件并命名为`GIVEN_NAME`,导入`PARA-NAME`组件
4. `importing all combination except Default Exports`
```
  import * as GIVEN_NAME from ADDRESS
```
从`ADDRESS`导入其所有的组件并命名为`GIVEN_NAME`，不包含默认组件
### 注
#### `ADDRESS`为一个相对路径，如果之间为组件名称，则在`node_modous`文件夹下搜索
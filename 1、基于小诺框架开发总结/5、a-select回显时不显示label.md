如下，数据回显的时候，显示的是`0`，而不是`中国`。
```vue
<!--
option-label-prop：指定回填内容
options：选项节点
-->
    <a-select
      v-model:value="myValue"
      style="width: 100%"
      placeholder="选择国家"
      option-label-prop="label"
      :options="options"
    >
      <template #option="{ value: val, label, icon }">
        &nbsp;&nbsp;{{ label }}
      </template>
    </a-select>
```

**将a-select的v-model绑定的数据的类型必须为字符串，否则不会显示标识。**

如下就不会显示：
```js
const options = ref([
  {
    value: 0,
    label: '中国',
  },
  {
    value: 1,
    label: '美国',
  },
  {
    value: 2,
    label: '日本',
  },
  {
    value: 3,
    label: '韩国',
  },
]);
```

要改为：
```js
const options = ref([
  {
    value: '0',
    label: '中国',
  },
  {
    value: '1',
    label: '美国',
  },
  {
    value: '2',
    label: '日本',
  },
  {
    value: '3',
    label: '韩国',
  },
]);
```

或者直接在数据库层面存字符串而不是数字：
```js
const options = ref([
  {
    value: 'china',
    label: '中国',
  },
  {
    value: 'usa',
    label: '美国',
  },
  {
    value: 'japan',
    label: '日本',
  },
  {
    value: 'korea',
    label: '韩国',
  },
]);
```
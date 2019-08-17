# iview-cascader-data
iview省市区级联选择数据

# 使用

```js
import province from '../../assets/js/regional_data/province'
import city from '../../assets/js/regional_data/city'
import country from '../../assets/js/regional_data/country'
import town from "../../assets/js/regional_data/town"
```

```html
<Cascader :data="addressData" :load-data="loadAddress"></Cascader>
```

```js
loadAddress(item, callback) {
    if (city[item.value]) {
        item.children = city[item.value];
    } else if (country[item.value]) {
        item.children = country[item.value];
    } else if (town[item.value]) {
        item.children = town[item.value];
    }
    if (!item.children) {
        this.$delete(item, "children");
        this.$delete(item, "loading");
    } else {
        item.loading = false;
    }
    callback();
}
```

> 一定要动态加载下级数据,否则会造成页面卡顿
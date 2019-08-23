# vue-simplemodal
モーダルコンテンツを簡易に実装するコンポーネント。  
[DEMO](https://large014.github.io/vue-simplemodal/)  

## Install
```
./src/components/modal/SimpleModal.vue をコピー
```

### Usage
```
import SimpleModal from './components/modal/SimpleModal.vue'

//--- <SimpleModal>タグの中に、クローズボタン、モーダルコンテンツを設定してください。
<SimpleModal ref="simplemodal" :color='"rgba(0,0,0, 0.35)"'>
    <CloseBtn slot="modalCloseBtn"/>
    <SimpleDialog slot="modalContents" title="これはテスト" msg="This will reset your device to its default factory settings." btn1_txt="CANCEL" btn2_txt="ACCEPT"/>
</SimpleModal>  

-----------------------------------------------------------

```
・プロパティ  
[color] モーダル表示時の背景色を設定します。  

・メソッド  
[show] モーダルコンテンツを表示  
[hide] モーダルコンテンツを表示  

・イベント  
$root.$emit('modal-hide-evt')"  

<SimpleModal>タグの中に設定したコンポーネントからモーダルを非表示にする場合は、  
下記のイベント通知してください。  
```


### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

https://youtu.be/ADxbGlwhl_s

powershell 관리자 권한으로 실행

```
Set-ExecutionPolicy RemoteSigned

Get-ExecutionPolicy
```

===

```
npm install -g @vue/cli

vue create .

```

===

vue에서 scss 적용하기

```
npm i node-sass@6.0.1 -D

npm i sass-loader@10.2.0 -D
```

```vue
<style lang="scss" scoped></style>
```

===

```
npm i axios
```

===

vue에서 프록시 설정으로 cors 해결

https://genie247.tistory.com/116

```javascript
module.exports = {
  devServer: {
    proxy: {
      "/api": {
        target: "http://localhost:3000",
      },
    },
  },
};
```

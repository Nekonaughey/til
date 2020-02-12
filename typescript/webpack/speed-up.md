
ts-loader is too slow.
特にproject-referencesしている場合。



@babel/preset-typescript
project-referencesに対応していなかった。
https://github.com/Microsoft/TypeScript-Babel-Starter/issues/35 - You don't have permissions to view 


fork-ts-checkerも相変わらずopenのまま。
https://github.com/TypeStrong/fork-ts-checker-webpack-plugin/issues/187 - You don't have permissions to view 


仕方ないので、
①tsc --watchで、noEmitにする。
②ts-loaderでtranspileonlyにする。
③①②を並行で動かす。(run-p)

⇒①でnoEmitにしたらproject referencesできない。型定義ファイルがないから。
emitDeclarationOnlyを使う手はあるが、速度は大差なし。



# 結論
tscでビルドして、webpackではトランスパイル済みのjsファイルを利用するのが一番早い。

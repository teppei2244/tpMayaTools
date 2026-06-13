# tpMayaTools

Maya tools collection for pipeline and rigging workflows.

## フォルダ構成

```
tpMayaTools/
├── modules/
│   └── tpMayaTools.mod   # Maya モジュール定義ファイル
├── scripts/              # Python スクリプト
├── icons/                # シェルフ用アイコン
└── plug-ins/             # Maya プラグイン
```

## インストール手順

### 1. リポジトリをクローン

任意の場所にクローンします。ここでは例として `C:\Users\<ユーザー名>\Documents\maya\modules` の親ディレクトリに置く方法を示します。

```bash
git clone https://github.com/teppei2244/tpMayaTools.git
```

### 2. modules フォルダを Maya に認識させる

Maya は環境変数 `MAYA_MODULE_PATH` に登録されたフォルダ内の `.mod` ファイルを自動で読み込みます。
以下のいずれかの方法で `tpMayaTools/modules` フォルダを登録してください。

#### 方法 A: Maya.env に追記（推奨）

Maya の設定フォルダにある `Maya.env` を開き、以下の行を追加します。

```
# Windows
MAYA_MODULE_PATH = C:\path\to\tpMayaTools\modules

# macOS / Linux
MAYA_MODULE_PATH = /path/to/tpMayaTools/modules
```

`Maya.env` の場所:
- **Windows:** `C:\Users\<ユーザー名>\Documents\maya\<バージョン>\Maya.env`
- **macOS:** `~/Library/Preferences/Autodesk/maya/<バージョン>/Maya.env`
- **Linux:** `~/maya/<バージョン>/Maya.env`

> すでに `MAYA_MODULE_PATH` が設定されている場合はセミコロン (Windows) またはコロン (Mac/Linux) で区切って追記してください。

#### 方法 B: modules フォルダにコピー

`tpMayaTools/modules/tpMayaTools.mod` を Maya のデフォルト modules フォルダにコピーし、`.mod` ファイル内のパスをクローン先の絶対パスに書き換えます。

```
+ tpMayaTools 1.0 C:\path\to\tpMayaTools
MAYA_SCRIPT_PATH +:= scripts
XBMLANGPATH +:= icons
MAYA_PLUG_IN_PATH +:= plug-ins
```

### 3. Maya を再起動

設定を反映するために Maya を再起動してください。

### 4. 動作確認

Maya のスクリプトエディタ (Python) で以下を実行してモジュールが認識されているか確認します。

```python
import maya.cmds as cmds
print(cmds.moduleInfo(listModules=True))
# 出力に "tpMayaTools" が含まれていれば成功
```

## 動作確認環境

- Maya 2022 / 2023 / 2024 / 2025
- Windows 10 / 11
- Python 3.x (Maya 同梱)

## ライセンス

MIT License

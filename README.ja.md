# POPL: Proof of Protocol Ledger

> **Languages:** [English](README.md) | 日本語

**POPL**は、AIプロトコル検証セッションを記録するための構造化台帳フォーマットです。「何が観測されたか？いつ？誰が？検証可能か？」に答えます。

## 思想

- **Proof of Protocol** = 観測可能で検証可能なAI通信の哲学
- **POPL** = それを永続化する台帳構造
- **POPL Entry** = 1検証セッション = 1記録

## リポジトリ構成

```
popl/
├── SPEC/                    # 仕様書
│   ├── popl-entry-v0.0.md   # エントリフォーマット定義
│   ├── levels.md            # 信頼レベル (0-3)
│   └── terminology.md       # 用語集
├── templates/               # すぐ使えるテンプレート
│   ├── POPL.yml             # エントリマニフェスト
│   └── EvidenceBlock.md     # ブログ記事用バッジ
├── validation-playbook/     # 検証セッションの実行方法
│   ├── principles.md        # 基本原則
│   ├── genspark/            # Genspark sandbox手順
│   └── local/               # ローカル実行ポリシー
└── VERSIONING.md            # バージョン履歴
```

## クイックスタート

1. [proofscan](https://github.com/proofofprotocol/proofscan)で**検証セッションを実行**
2. **成果物をキャプチャ**: `events.json`, `tree.json`, `RUNLOG.md`
3. [templates/POPL.yml](templates/POPL.yml)を使って**POPL.ymlを作成**
4. proofscanの`validation/session-YYYY-MM-DD-<target>/`に**コミット**
5. **公証**（任意）: [inscribe-mcp](https://github.com/inscribepop/inscribe-mcp)でIPFS + Hedera HCS

## 証拠の格納場所

| 種類 | 場所 |
|------|------|
| 仕様・テンプレート・手順書 | このリポジトリ (`popl`) |
| 証拠成果物 | [proofscan/validation/](https://github.com/proofofprotocol/proofscan/tree/main/validation) |
| 人が読む記事 | [POP@AI](https://note.com/pop_ai/) |
| 公証レイヤー | [inscribe-mcp](https://github.com/inscribepop/inscribe-mcp) |

## 信頼レベル

| レベル | 名称 | 証明内容 | 必須 |
|--------|------|----------|------|
| 0 | Recorded | Gitコミットが存在 | Yes |
| 1 | Notarized | IPFS + Hederaタイムスタンプ | Yes |
| 2 | Attributed | DID/署名が付与 | No |
| 3 | Third-party | 第三者検証 | No |

詳細は[SPEC/levels.md](SPEC/levels.md)を参照。

## 主要リンク

- [SPEC/popl-entry-v0.0.md](SPEC/popl-entry-v0.0.md) - エントリフォーマット仕様
- [templates/POPL.yml](templates/POPL.yml) - すぐ使えるテンプレート
- [validation-playbook/genspark/sandbox-instructions.md](validation-playbook/genspark/sandbox-instructions.md) - Genspark実行ガイド

## ライセンス

MIT

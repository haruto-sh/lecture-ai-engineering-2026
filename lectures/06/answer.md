# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：glossary_search_glossary
- STEP 2 の [tool call]：glossary_search_glossary({'query': '3レベル'})
- STEP 3 の [tool call]：fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
- STEP 4 の [tool call]：
  - aws_aws___search_documentation({'search_phrase': 'Amazon S3 バージョニング 概要', 'topics': ['general']})
  - aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Using versioning in S3 buckets'})
- 気づき・疑問：自分の環境で起動するサーバー（glossary、fetch）と、URLで接続する外部サーバー（aws）の両方を同じエージェントから利用できた。

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：基礎
- やったこと：`app/mcp_server.py` に `server.tool()(tools.get_lecture_summary)` を追加して、講義要約ツールを公開した。
- 結果：一覧に `glossary_get_lecture_summary` が追加された。質問「第2回では何を学びますか？」で `glossary_get_lecture_summary({'lecture': 2})` が呼び出され、第2回の要点が返った。`uv run pytest -q` は 21 件すべて成功。
- 気づき・疑問：サーバー側にツールを登録するだけで、エージェント側のコードや設定を変えずに利用できた。

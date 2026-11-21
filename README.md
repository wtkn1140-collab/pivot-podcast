# PIVOT 公式チャンネル 音声版

YouTube「PIVOT 公式チャンネル」（@pivot00）の動画を音声化し、Apple Podcasts で聴けるようにする仕組み。
構成は `~/claude/ryogakucho-podcast` と同じ（取得は Mac、配信は GitHub Pages）。

## スマホで聴く
- フィード: https://wtkn1140-collab.github.io/pivot-podcast/feed.xml
  （Apple Podcasts → ライブラリ →「…」→「URLで番組をフォロー」）
- プレーヤー: https://wtkn1140-collab.github.io/pivot-podcast/

## Mac 側
- 自動実行: `~/Library/LaunchAgents/com.pivot.podcast.plist` → `run.sh`（2時間ごと）
- ログ: `logs/update.log`
- 手動で今すぐ取得: `./run.sh`
- 自動実行を止める: `launchctl bootout gui/$(id -u) ~/Library/LaunchAgents/com.pivot.podcast.plist`
- 最新15本は `audio-site/`（pivot-podcast-audio）、それより前（最新100本まで）は `archive1/`〜（pivot-podcast-archiveN）
- 題名は日本語で取得するため `youtube:lang=ja` を指定している
- 特定の言葉を含む動画を除外したいときは `podcast.py` の `EXCLUDE_WORDS` に書く

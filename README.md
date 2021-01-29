* chrome のフラグ `chrome://flags` の差分を追いやすくするための置き場
* (利用例) `260ef2aadf49` とかに git checkout して下のように実行すれば chrome87 から 88 の間に追加 / 削除されたフラグ名が一望出来る (はず)
```bash
git diff HEAD@{1} chrome_flags.csv | grep "^\(-\|+\)" | awk -F ',' {'print $1'} | sort -t '#' -k 2 | uniq -s 1 -c | grep "^   1" | awk -F ' ' '{print $2}' | sort

# 上記実行結果。 +#~~ が新規追加されたフラグ、-#~~ が削除されたフラグ
# +#check-offline-capability
# +#cookies-page-redesign
# ... (中略)
# +#use-first-party-set
# +++
# -#align-font-display-auto-lcp
# ... (中略)
# -#temporary-unexpire-flags-m85
# ---
```

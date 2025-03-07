
#!/bin/bash

# Toplam commit sayısını al
TOTAL_COMMITS=$(git rev-list --all --count)

# En çok commit atan kişiyi bul
TOP_CONTRIBUTOR=$(git log --format='%an' | sort | uniq -c | sort -nr | head -n 1)

# README.md'yi güncelle
sed -i '/<!-- GIT_STATS_START -->/,/<!-- GIT_STATS_END -->/d' README.md

echo "<!-- GIT_STATS_START -->" >> README.md
echo "## Git İstatistikleri" >> README.md
echo "**Toplam Commit Sayısı:** $TOTAL_COMMITS" >> README.md
echo "**En Çok Commit Atan Kişi:** $TOP_CONTRIBUTOR" >> README.md
echo "<!-- GIT_STATS_END -->" >> README.md

echo "README.md başarıyla güncellendi!"

# 以官方 n8n image 為基礎
FROM n8nio/n8n:latest

# 先切到 root，才能安裝套件
USER root

# 安裝 fontconfig，讓系統可以管理字型
RUN apt-get update && \
    apt-get install -y fontconfig && \
    rm -rf /var/lib/apt/lists/*

# 建立一個自訂字型資料夾（如果不存在）
RUN mkdir -p /usr/share/fonts/truetype/custom

# 把你 GitHub repo 裡的中文字型複製進 image 裡
COPY fonts/NotoSansTC-VariableFont_wght.ttf /usr/share/fonts/truetype/custom/

# 更新字型快取，讓系統認得這個新字型
RUN fc-cache -f -v

# 切回預設的 node 使用者，n8n 正常啟動
USER node

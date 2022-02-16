ARG FRAPPE_BRANCH=develop
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

ARG GITHUB_OWNER=default_github_owner # you could give a default value as well
ENV GITHUB_OWNER=$GITHUB_OWNER

RUN install_app metabase_integration https://github.com/${GITHUB_OWNER}/ERPNext-Metabase-Integration master && \
  install_app erpnext_telegram_integration https://github.com/${GITHUB_OWNER}/ERPNext-Telegram-Integration master && \
  install_app barcode_shrdc https://github.com/${GITHUB_OWNER}/ERPNext-Barcode-Integration master && \
  install_app frepple https://github.com/${GITHUB_OWNER}/ERPNext-Frepple-Integration master
  

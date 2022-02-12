ARG FRAPPE_BRANCH=develop
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

ARG GITHUB_OWNER=default_github_owner # you could give a default value as well
ENV GITHUB_OWNER=$GITHUB_OWNER

RUN install_app metabase_integration https://github.com/${GITHUB_OWNER}/shrdc_frappe_metabase master && \
  install_app erpnext_telegram_integration https://github.com/${GITHUB_OWNER}/shrdc_erpnext_telegram master && \
  install_app barcode_shrdc https://github.com/leexy0/barcode_shrdc master && \
  install_app frepple https://github.com/Drayang/ERPNext-Frepple master && \
  install_app my_custom_maintenance https://github.com/msf4-0/ERPNext_my_custom__maintenance master
  

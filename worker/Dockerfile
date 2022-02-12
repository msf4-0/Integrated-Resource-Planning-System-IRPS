ARG FRAPPE_BRANCH=develop
ARG GITHUB_OWNER=default_github_owner
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

RUN install_app metabase_integration https://github.com/${GITHUB_OWNER}/shrdc_frappe_metabase master && \
  install_app bench_manager https://github.com/${GITHUB_OWNER}/shrdc_bench_manager develop && \
  install_app erpnext_telegram_integration https://github.com/${GITHUB_OWNER}/shrdc_erpnext_telegram master && \
  install_app barcode_shrdc https://github.com/leexy0/barcode_shrdc master && \
  install_app frepple https://github.com/Drayang/ERPNext-Frepple master && \
  install_app my_custom_maintenance https://github.com/msf4-0/ERPNext_my_custom__maintenance master
  

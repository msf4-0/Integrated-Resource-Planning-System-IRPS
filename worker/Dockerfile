ARG FRAPPE_BRANCH=develop
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

RUN install_app metabase_integration https://github.com/${GITHUB_OWNER}/shrdc_frappe_metabase master && \
  install_app bench_manager https://github.com/${GITHUB_OWNER}/shrdc_bench_manager develop

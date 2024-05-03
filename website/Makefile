deps:
	git submodule update --init --recursive
	rsync -av ../ root/ --include='assessments' --include='governance' --include='governance/related-groups' --include='supply-chain-security' --include='*.md' --exclude='*'
	rsync -av '../design/' 'static/design/' --exclude='#*'

	cd root/ &&\
	for file in ./*; do \
		BASE_NAME=$${file##*/}; \
		BASE_NAME=$${BASE_NAME%.*}; \
		TEXT_TO_PREPEND="---\ntitle: \"$$BASE_NAME\"\n---\n"; \
		sed '1d' "$$file" > temp_file; \
		echo "$$TEXT_TO_PREPEND" | cat - temp_file > temp_file_with_header && mv temp_file_with_header "$$file"; \
	done
	mv root/* content/

serve: deps
	hugo server \
		--disableFastRender \
		--buildDrafts \
		--buildFuture \
		--ignoreCache
		--printI18nWarnings \
		--printMemoryUsage \
		--printPathWarnings \
		--printUnusedTemplates \
		--templateMetrics \
		--templateMetricsHints \
		--gc

production-build: deps
	hugo \
		--minify
	npx -y pagefind --site public

preview-build: deps
	hugo \
		--baseURL $(DEPLOY_PRIME_URL) \
		--buildDrafts \
		--buildFuture \
		--minify
	npx -y pagefind --site public
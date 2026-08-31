# Changelog

## [3.1.1](https://github.com/theholocron/.github/compare/v3.1.0...v3.1.1) (2026-08-31)


### Bug Fixes

* 🐛 add DCO probot config to allow remediation commits ([#177](https://github.com/theholocron/.github/issues/177)) ([477edb4](https://github.com/theholocron/.github/commit/477edb406123b091468699324afcf6450dd5b109))

## [3.1.0](https://github.com/theholocron/.github/compare/v3.0.0...v3.1.0) (2026-08-27)


### Features

* ✨ add Release Please tag workflow ([#158](https://github.com/theholocron/.github/issues/158)) ([5948a2a](https://github.com/theholocron/.github/commit/5948a2ab7b04112d4694e70ccfc2e3f6470630d2))
* 👷 add in community health files ([02d9c13](https://github.com/theholocron/.github/commit/02d9c13651c4947d686785df774bdd389b620695))
* 👷 add in github workflow action templates ([ce5d5b1](https://github.com/theholocron/.github/commit/ce5d5b13d0c63d66db5116c53943acdb1d1eba5c))
* 👷 bring parity with ci system ([2bfb940](https://github.com/theholocron/.github/commit/2bfb940ce6bed471f61075e3cdac0076d13796b9))
* 📝 add in public organization profile ([0bb88d3](https://github.com/theholocron/.github/commit/0bb88d3e45f276515003a40b57c9a88d94344c7e))
* 📝 update to use doc sites links ([733734a](https://github.com/theholocron/.github/commit/733734a33b4a6a3c879ef0c3cc553fd59e93383d))
* add profile picture ([f95cfd5](https://github.com/theholocron/.github/commit/f95cfd5b935b942b8e3872b57a66ad6cefd290d7))
* add reusable CI workflows, composite actions, and workflow templates ([d33a84c](https://github.com/theholocron/.github/commit/d33a84c685b43fd43d2f61c1320389369b30b66c))
* **deploy:** add storybook-projects and single-job assembly with sandbox/ paths ([#126](https://github.com/theholocron/.github/issues/126)) ([44c7bde](https://github.com/theholocron/.github/commit/44c7bde12514b86380d3a55a4371c02aec92a0ba))
* **deploy:** replace per-type reusable workflows with unified deploy.yml ([#124](https://github.com/theholocron/.github/issues/124)) ([0851bf3](https://github.com/theholocron/.github/commit/0851bf3204c7c4549576e2100d08d41466df0415))
* reusable CI infrastructure — workflows, actions, templates, security ([#12](https://github.com/theholocron/.github/issues/12)) ([f03cbb9](https://github.com/theholocron/.github/commit/f03cbb94293c083fc876445b1ee4a14fb3671511))


### Bug Fixes

* add in sync token ([#63](https://github.com/theholocron/.github/issues/63)) ([a5b8015](https://github.com/theholocron/.github/commit/a5b80150250ec0e9f67753ddad9a7ca0c90e96d8))
* change out token ([#62](https://github.com/theholocron/.github/issues/62)) ([a7c4619](https://github.com/theholocron/.github/commit/a7c4619284177a04d41cc1c5f27acfcd6d6a79bf))
* **ci:** 🐛 drop --with-deps from playwright install ([#138](https://github.com/theholocron/.github/issues/138)) ([2a73533](https://github.com/theholocron/.github/commit/2a735338cc93ff952b818f08eb612565d3ba6be4))
* **ci:** 🐛 use secrets: inherit so dynamic token names resolve correctly ([#139](https://github.com/theholocron/.github/issues/139)) ([f210ca2](https://github.com/theholocron/.github/commit/f210ca2a15b739487d6df8efb34ed00a59e66262))
* **ci:** restrict interaction job to chromium only to match storybook job ([#135](https://github.com/theholocron/.github/issues/135)) ([7048e8c](https://github.com/theholocron/.github/commit/7048e8c35971ebb3d78781faf1ed97b00b0c8a6f))
* **ci:** scope GIT_COMMITLINT to PR base ref, not repo default branch ([#28](https://github.com/theholocron/.github/issues/28)) ([f666052](https://github.com/theholocron/.github/commit/f66605293a74b122a63bf654f089a5231eca6a11))
* clear NODE_AUTH_TOKEN so OIDC Trusted Publishing can authenticate ([#75](https://github.com/theholocron/.github/issues/75)) ([70b28fb](https://github.com/theholocron/.github/commit/70b28fbd5b7608d9b5e7605191cea494b24b3970))
* **lint:** do not auto-enable ESLint via super-linter ([62aaeaf](https://github.com/theholocron/.github/commit/62aaeaf26184a9a87eeada59775e59108d8231a8))
* **lint:** skip JS/TS ESLint when eslint config file is absent ([#114](https://github.com/theholocron/.github/issues/114)) ([71bcfec](https://github.com/theholocron/.github/commit/71bcfecb63001fc6751b3aa0e564e2b254880b9c))
* **lint:** use detect step output to gate ESLint config and VALIDATE_ flags ([#116](https://github.com/theholocron/.github/issues/116)) ([d8c3fb4](https://github.com/theholocron/.github/commit/d8c3fb4f7babf1d6a50ce6937c557089f71bded1))
* **lint:** use empty string not false for off-state VALIDATE_* vars ([7c5e211](https://github.com/theholocron/.github/commit/7c5e21163782292df83fe0de1296d0245a75e198))
* **lint:** use empty string not false for off-state VALIDATE_* vars ([#117](https://github.com/theholocron/.github/issues/117)) ([91d8235](https://github.com/theholocron/.github/commit/91d82356ad9749a27df997802ae83aa899bddf55))
* **lint:** use GPG key identity for auto-commit user and signed-off-by ([#70](https://github.com/theholocron/.github/issues/70)) ([f290407](https://github.com/theholocron/.github/commit/f29040703c63fa9cf45775d25dbdcd9c822eb4a8))
* make Cypress wait-on URL configurable via wait-on-url input ([#111](https://github.com/theholocron/.github/issues/111)) ([a7e6c0b](https://github.com/theholocron/.github/commit/a7e6c0bba3c94417ce64763ef12c3cbcefa93790))
* replace VALIDATE_CSS opt-in with always-on, drop enable-stylelint input ([6c332e6](https://github.com/theholocron/.github/commit/6c332e69d52458931fc59ff9d0bd064afd314e7b))
* **test:** revert secrets: inherit — fixes workflow file issue on PR events ([#140](https://github.com/theholocron/.github/issues/140)) ([dfe4fce](https://github.com/theholocron/.github/commit/dfe4fce3ddb4a4e970d45389cd2e74423f07e73d))


### Performance Improvements

* **ci:** cache Playwright browsers and bump storybook/interaction timeouts to 20m ([#134](https://github.com/theholocron/.github/issues/134)) ([e3b42c0](https://github.com/theholocron/.github/commit/e3b42c08f428e3ed97a1279e8b5db876d0b6491a))
* **ci:** skip playwright install-deps on cache hit — ubuntu-24.04 has chromium deps ([#137](https://github.com/theholocron/.github/issues/137)) ([244dd66](https://github.com/theholocron/.github/commit/244dd66ac9dd50aebf734a4e61b1551ffbe31587))

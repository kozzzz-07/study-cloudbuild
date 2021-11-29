# CD のサンプル PJ

- CloudBuild で CD を行うサンプル

- Dev→Prod の流れを意識している

### Cloud Build

- 注意点

  - `--allow-unauthenticated` 認証必要なしで UP するにはサービスアカウントには CloudRun の管理者が必要
    - https://cloud.google.com/run/docs/authenticating/public#command-line
  - Artifact Registry にアップする際は先にリポジトリを作成しておく必要がある
  - ローカルで実行する際は、SHORT_SHA を自前で付与する必要がある
    - (bash 利用想定)
    - server
      - `gcloud builds submit --config=./server/cloudbuild.yaml --substitutions=SHORT_SHA="$(git rev-parse --short HEAD)"`
    - client
      - `gcloud builds submit --config=./client/sample-app/cloudbuild.yaml --substitutions=SHORT_SHA="$(git rev-parse --short HEAD)"`

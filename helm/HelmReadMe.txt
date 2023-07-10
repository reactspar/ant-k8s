This is the instruction how to switch all charts to another helm repo.

# First we need to remove all http refferences to old chart repo.
## Go to every chart and clear its "chats" folder. It is needed because archived dependencies have an old http refference to the old repo.
## Go to every Chart.yaml of every chart and update "dependencies.repository" url to reffer to the new repo.

#No you can start updating and deploying. Here we use http://localhost:8087 as a new chart repo.


# go to helm directory
cd <project_folder>/helm

# start HTTP server on charts folder
python -m http.server --bind 127.0.0.1 8087 -d charts


# Here probably you need to open a separate CLI because of python is not in background. In this case navigate again to helm folder before proceeding.

# delete previouse repo
helm repo remove mycharts

# add index file to the charts folder to mark it as a repository
helm repo index charts

# add local repo
helm repo add mycharts http://localhost:8087

# install zookeeper
helm package zookeeper --destination charts
helm repo index charts
helm repo update mycharts

# install kafka
helm dependency update kafka
helm package kafka --destination charts
helm repo index charts
helm repo update mycharts


# install schema-registry
helm dependency update schema-registry
helm package schema-registry --destination charts
helm repo index charts
helm repo update mycharts


# install mongo-db
helm dependency update mongo-db
helm package mongo-db --destination charts
helm repo index charts
helm repo update mycharts

# install chat-api
helm dependency update chat-api
helm package chat-api --destination charts
helm repo index charts
helm repo update mycharts

# install chat-ui
helm dependency update chat-ui
helm package chat-ui --destination charts
helm repo index charts
helm repo update mycharts

# Verify that you have all installed charts in mycharts local repo
helm search repo mycharts

# start chat-ui helm. And it should start all its dependencies.
helm install chat-ui mycharts/chat-ui
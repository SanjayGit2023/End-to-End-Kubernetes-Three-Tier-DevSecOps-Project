
                            git config user.email "sanjaychettri54@gmail.com"
                            git config user.name "Sanjay-DevOps"
                            BUILD_NUMBER=${BUILD_NUMBER}
                            echo $BUILD_NUMBER
                            imageTag=$(grep -oP '(?<=backend:)[^ ]+' deployment.yaml)
                            echo $imageTag
                            sed -i "s/${AWS_ECR_REPO_NAME}:${imageTag}/${AWS_ECR_REPO_NAME}:${BUILD_NUMBER}/" deployment.yaml
                            git status  # Check the status of files
                            git add -A  # Stage all changes, including new files
                            git commit -m "Update deployment Image to version ${BUILD_NUMBER}" || echo "No changes to commit"
                            git push https://${GITHUB_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME}.git HEAD:master
                        
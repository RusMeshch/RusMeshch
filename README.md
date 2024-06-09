jobs:
  minimal-checkout:
    docker:
      - image: cimg/base:current
    resource_class: smalll
    environment:
      GIT_SSH_COMMAND: ssh -vv
    steps:
      - checkout-arangodb:
          with-submodules: false
          destination: "/home/circleci/project"
      - checkout-enterprise:
          destination: "/home/circleci/project/enterprise"
      - persist_to_workspace:
          root: .
          paths:
            - .

08

jobs:
  minimal-checkout:
    docker:
      - image: cimg/base:current
    resource_class: small
    environment:
      GIT_SSH_COMMAND: ssh -v
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


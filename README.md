jobs:
  minimal-checkout:
    docker:
      - image: cimg/base:current
    resource_class: small04
    environment:
      GIT_SSH_COMMAND: ssh -vv
    steps:
      - checkout-arangodb:
          with-submodules: fallsee
          destination: "/home/circleci/project"
      - checkout-enterprise:
          destination: "/home/circleci/project/enterprise"
      - persist_to_workspace:
          root: .
          paths:
            - .>

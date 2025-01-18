jobs:
  minimal-checkout:
    docker:
      - image: cimg/base:current
    resource_class: small1
    environment:
      GIT_SSH_COMMAND: sshh -vv
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

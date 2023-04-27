# AWS Guard Rules Registry

AWS Guard Rules Registry is an open-source repository of [AWS CloudFormation Guard](https://github.com/aws-cloudformation/cloudformation-guard) rule files and managed rule sets that help organizations *shift left* in their Software Development Life Cycle (SDLC) processes.

## TL;DR

**Leverage the existing AWS Guard Registry Rule Sets currently available:**
* Read the [Using Guard Rules Registry Guide](./docs/Using-Guard-Rules-Registry.md) for information on how to integrate into your existing continuous integration and development processes. Then pick from the list of [Guard Rules Registry Managed Rule Sets](#managed-rule-sets).

**Contribute to the individual AWS Guard Registry Rules:**
* Read the [Guard Rules Development Guide](./docs/Guard-Rules-Dev-Guide.md) for details in how to contribute and develop Guard Rules Registry rules. Additionally, Guard Rules Registry has several staged Guard rule files that have yet to be implemented. These Guard rules are to be a *best of effort* representation of AWS Config Managed rules. To get started look for an open issues labeled `good first issue`.

**Create and contribute your own open source AWS Guard Rules Registry custom rule set:**
* Read the [Guard Rule Sets Development Guide](./docs/Guard-Rule-Sets-Dev-Guide.md) for details on creating or updating the Guard Map rule set files.

## About

AWS Guard Rules Registry is an open-source repository of rule files and managed rule sets for AWS CloudFormation Guard. The intent of the registry is to give users Guard rules that provide policy as code solutions which complement the AWS Config Managed Rules as well as your Guard rules. Many of the Guard rules supported by AWS are best-effort Guard rule implementations of AWS Config Managed Rules.

> **Note:** Not all AWS Config Managed Rules are present in the AWS Guard Rules Registry. Some of the AWS Config Managed Rules are detective only in nature and are not able to be expressed in infrastructure as code relevant to development practices.

The Guard Rules Registry offers the following value:

* Easy to consume Managed Rules Sets based on many of the sample AWS Conformance Packs. *see [Guard Rules Registry Managed Rule Sets](#managed-rule-sets)*
* Individual Guard Rule files giving *best effort* to correspond to an AWS Config Managed Rule
* Rule Set mapping process to compile single rule set files for public consumption
* A centralized location for users, teams, and organizations to manage and open source their custom Guard rule sets
* Resource level rule suppress! See [Using Guard Rules Registry Rule Suppression](./docs/Using-Guard-Rules-Registry.md#guard-rules-registry-rule-suppression) for more details.

### Registry Rules Files

One of the intents of AWS Guard Rules Registry is to create modular single file Guard rule files that can be mapped into multiple managed rule sets similar to how AWS Config Conformance Packs work with AWS Config Managed Rules. The AWS Guard Rules Registry contains individual guard rule files associated to a single rule. The [rules directory](/rules) contains multiple sub-directories based on different technologies, providers, and services.

    ```
    rules
    ├── aws
    │   └── apigateway
    │   │   ├── apigw_method_auth_type_is_not_none.guard
    │   │   └── tests
    │   │       └── apigw_method_auth_type_is_not_none_tests.yml
    │   └── dynamodb
    │       ├── dynamodb_pitr_enabled.guard
    │       └── tests
    │           └── dynamodb_pitr_is_enabled_tests.yml
    ├── kubernetes
    └── terraform
    ```

Many of the Guard rules are supported by AWS and correspond or complement associated AWS Config Managed Rules. These rules can be identified by the all-uppercase naming convention which is identical to the AWS Config Managed Rule identifier.

> **Note:** Guard rule names that are in all uppercase are intentionally set this way. The names reflects the AWS Config Managed rule identifier the guard rule is satisfying.

Within each directory that contains Guard rules, there is a `tests` sub-directory contains unit tests for some of the corner cases we expect Guard rule to `PASS`/`FAIL`/`SKIP`. The `test` sub-directory contains the corresponding test file for the Guard rule with the suffix `_tests` and can have the extension of `.yml` or `.json`. To learn more, see [Guard Rules Dev Guide](./docs/Guard-Rules-Dev-Guide.md#writing-unit-tests) for more detail on how to create unit tests for your guard rule.

### Managed Rule Sets

AWS Guard Rules registry contains prebuilt managed rule sets compiled from rule mapping files found in the [mappings](/mappings) directory. The following managed Rule Sets are available for use:

| Managed Rule Set                         | Rules Set Name | Mapping File |
| -------------------------------- | -------- | ---------- |
| Payment Card Industry Data Security Standard (PCI DSS) 3.2.1 | PCI-DSS-3-2-1 | [Link](/mappings/rule_set_grc351_pci_dss_3_2_1.json) |


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This project is licensed under the [Apache-2.0 License](LICENSE).


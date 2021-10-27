## API Report File for "@backstage/plugin-permission-node"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
import { AuthorizeRequest } from '@backstage/plugin-permission-common';
import { AuthorizeResult } from '@backstage/plugin-permission-common';
import { BackstageIdentity } from '@backstage/plugin-auth-backend';
import { PermissionCondition } from '@backstage/plugin-permission-common';
import { PermissionCriteria } from '@backstage/plugin-permission-common';
import { Router } from 'express';

// @public
export type ApplyConditionsRequest = {
  resourceRef: string;
  resourceType: string;
  conditions: PermissionCriteria<PermissionCondition>;
};

// Warning: (ae-unresolved-link) The @link reference could not be resolved: The package "@backstage/plugin-permission-node" does not have an export "AuthorizeResult"
//
// @public
export type ConditionalPolicyResult = {
  result: AuthorizeResult.CONDITIONAL;
  conditions: {
    pluginId: string;
    resourceType: string;
    conditions: PermissionCriteria<PermissionCondition>;
  };
};

// Warning: (ae-missing-release-tag) "conditionFor" is exported by the package, but it is missing a release tag (@alpha, @beta, @public, or @internal)
//
// @public (undocumented)
export const conditionFor: <TParams extends any[]>(
  rule: PermissionRule<unknown, unknown, TParams>,
) => (...params: TParams) => {
  rule: string;
  params: TParams;
};

// Warning: (ae-missing-release-tag) "createPermissionIntegration" is exported by the package, but it is missing a release tag (@alpha, @beta, @public, or @internal)
//
// @public (undocumented)
export const createPermissionIntegration: <
  TResource,
  TRules extends {
    [key: string]: PermissionRule<TResource, any, unknown[]>;
  },
  TGetResourceParams extends any[] = [],
>({
  pluginId,
  resourceType,
  rules,
  getResource,
}: {
  pluginId: string;
  resourceType: string;
  rules: TRules;
  getResource: (
    resourceRef: string,
    ...params: TGetResourceParams
  ) => Promise<TResource | undefined>;
}) => {
  createPermissionIntegrationRouter: (...params: TGetResourceParams) => Router;
  toQuery: (
    conditions: PermissionCriteria<PermissionCondition>,
  ) => PermissionCriteria<QueryType<TRules>>;
  conditions: Conditions<TRules>;
  createConditions: (conditions: PermissionCriteria<PermissionCondition>) => {
    pluginId: string;
    resourceType: string;
    conditions: PermissionCriteria<PermissionCondition>;
  };
  registerPermissionRule: (
    rule: PermissionRule<TResource, QueryType<TRules>, unknown[]>,
  ) => void;
};

// @public
export interface PermissionPolicy {
  // Warning: (ae-forgotten-export) The symbol "PolicyAuthorizeRequest" needs to be exported by the entry point index.d.ts
  //
  // (undocumented)
  handle(
    request: PolicyAuthorizeRequest,
    user?: BackstageIdentity,
  ): Promise<PolicyResult>;
}

// Warning: (ae-unresolved-link) The @link reference could not be resolved: The package "@backstage/plugin-permission-node" does not have an export "AuthorizeResult"
//
// @public
export type PermissionRule<
  TResource,
  TQuery,
  TParams extends unknown[] = unknown[],
> = {
  name: string;
  description: string;
  apply(resource: TResource, ...params: TParams): boolean;
  toQuery(...params: TParams): PermissionCriteria<TQuery>;
};

// @public
export type PolicyResult =
  | {
      result: AuthorizeResult.ALLOW | AuthorizeResult.DENY;
    }
  | ConditionalPolicyResult;

// Warnings were encountered during analysis:
//
// src/integration/createPermissionIntegration.d.ts:28:5 - (ae-forgotten-export) The symbol "QueryType" needs to be exported by the entry point index.d.ts
// src/integration/createPermissionIntegration.d.ts:29:5 - (ae-forgotten-export) The symbol "Conditions" needs to be exported by the entry point index.d.ts
```
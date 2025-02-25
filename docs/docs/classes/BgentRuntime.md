---
id: "BgentRuntime"
title: "Class: BgentRuntime"
sidebar_label: "BgentRuntime"
sidebar_position: 0
custom_edit_url: null
---

Represents the runtime environment for an agent, handling message processing,
action registration, and interaction with external services like OpenAI and Supabase.

## Constructors

### constructor

• **new BgentRuntime**(`opts`): [`BgentRuntime`](BgentRuntime.md)

Creates an instance of BgentRuntime.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `opts` | `Object` | The options for configuring the BgentRuntime. |
| `opts.actions?` | [`Action`](../interfaces/Action.md)[] | Optional custom actions. |
| `opts.debugMode?` | `boolean` | If true, debug messages will be logged. |
| `opts.evaluators?` | [`Evaluator`](../interfaces/Evaluator.md)[] | Optional custom evaluators. |
| `opts.providers?` | [`Provider`](../interfaces/Provider.md)[] | Optional context providers. |
| `opts.recentMessageCount?` | `number` | The number of messages to hold in the recent message cache. |
| `opts.serverUrl?` | `string` | The URL of the worker. |
| `opts.supabase` | `default`\<`any`, ``"public"``, `any`\> | The Supabase client. |
| `opts.token` | `string` | The JWT token, can be a JWT token if outside worker, or an OpenAI token if inside worker. |

#### Returns

[`BgentRuntime`](BgentRuntime.md)

## Properties

### actions

• **actions**: [`Action`](../interfaces/Action.md)[] = `[]`

Custom actions that the agent can perform.

___

### debugMode

• **debugMode**: `boolean`

Indicates if debug messages should be logged.

___

### descriptionManager

• **descriptionManager**: [`MemoryManager`](MemoryManager.md)

Store and recall descriptions of users based on conversations.

___

### evaluators

• **evaluators**: [`Evaluator`](../interfaces/Evaluator.md)[] = `[]`

Evaluators used to assess and guide the agent's responses.

___

### factManager

• **factManager**: [`MemoryManager`](MemoryManager.md)

Manage the fact and recall of facts.

___

### loreManager

• **loreManager**: [`MemoryManager`](MemoryManager.md)

Manage the creation and recall of static information (documents, historical game lore, etc)

___

### messageManager

• **messageManager**: [`MemoryManager`](MemoryManager.md)

Store messages that are sent and received by the agent.

___

### providers

• **providers**: [`Provider`](../interfaces/Provider.md)[] = `[]`

Context providers used to provide context for message generation.

___

### serverUrl

• **serverUrl**: `string` = `"http://localhost:7998"`

The base URL of the server where the agent's requests are processed.

___

### supabase

• **supabase**: `default`\<`any`, ``"public"``, `any`\>

The Supabase client used for database interactions.

___

### token

• **token**: ``null`` \| `string`

Authentication token used for securing requests.

## Methods

### completion

▸ **completion**(`opts`): `Promise`\<`string`\>

Send a message to the OpenAI API for completion.

#### Parameters

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `opts` | `Object` | `undefined` | The options for the completion request. |
| `opts.context` | `undefined` \| `string` | `""` | The context of the message to be completed. |
| `opts.frequency_penalty` | `undefined` \| `number` | `0.0` | The frequency penalty to apply to the completion. |
| `opts.model` | `undefined` \| `string` | `"gpt-3.5-turbo-0125"` | The model to use for completion. |
| `opts.presence_penalty` | `undefined` \| `number` | `0.0` | The presence penalty to apply to the completion. |
| `opts.stop` | `undefined` \| `never`[] | `[]` | A list of strings to stop the completion at. |

#### Returns

`Promise`\<`string`\>

The completed message.

___

### composeState

▸ **composeState**(`message`): `Promise`\<\{ `actionConditions`: `string` ; `actionExamples`: `string` ; `actionNames`: `string` ; `actions`: `string` ; `actors`: `string` ; `actorsData`: [`Actor`](../interfaces/Actor.md)[] ; `agentId`: \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` ; `agentName`: `undefined` \| `string` ; `evaluatorConditions`: `string` ; `evaluatorExamples`: `string` ; `evaluatorNames`: `string` ; `evaluators`: `string` ; `evaluatorsData`: [`Evaluator`](../interfaces/Evaluator.md)[] ; `goals`: `string` ; `goalsData`: [`Goal`](../interfaces/Goal.md)[] ; `lore`: `string` ; `loreData`: [`Memory`](../interfaces/Memory.md)[] ; `providers`: `string` ; `recentFacts`: `string` ; `recentFactsData`: [`Memory`](../interfaces/Memory.md)[] ; `recentMessages`: `string` ; `recentMessagesData`: [`Memory`](../interfaces/Memory.md)[] ; `relevantFacts`: `string` ; `relevantFactsData`: [`Memory`](../interfaces/Memory.md)[] ; `room_id`: \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` ; `senderName`: `undefined` \| `string` ; `userIds`: \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\`[]  }\>

Compose the state of the agent into an object that can be passed or used for response generation.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `message` | [`Message`](../interfaces/Message.md) | The message to compose the state from. |

#### Returns

`Promise`\<\{ `actionConditions`: `string` ; `actionExamples`: `string` ; `actionNames`: `string` ; `actions`: `string` ; `actors`: `string` ; `actorsData`: [`Actor`](../interfaces/Actor.md)[] ; `agentId`: \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` ; `agentName`: `undefined` \| `string` ; `evaluatorConditions`: `string` ; `evaluatorExamples`: `string` ; `evaluatorNames`: `string` ; `evaluators`: `string` ; `evaluatorsData`: [`Evaluator`](../interfaces/Evaluator.md)[] ; `goals`: `string` ; `goalsData`: [`Goal`](../interfaces/Goal.md)[] ; `lore`: `string` ; `loreData`: [`Memory`](../interfaces/Memory.md)[] ; `providers`: `string` ; `recentFacts`: `string` ; `recentFactsData`: [`Memory`](../interfaces/Memory.md)[] ; `recentMessages`: `string` ; `recentMessagesData`: [`Memory`](../interfaces/Memory.md)[] ; `relevantFacts`: `string` ; `relevantFactsData`: [`Memory`](../interfaces/Memory.md)[] ; `room_id`: \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\` ; `senderName`: `undefined` \| `string` ; `userIds`: \`$\{string}-$\{string}-$\{string}-$\{string}-$\{string}\`[]  }\>

The state of the agent.

___

### embed

▸ **embed**(`input`): `Promise`\<`number`[]\>

Send a message to the OpenAI API for embedding.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `input` | `string` | The input to be embedded. |

#### Returns

`Promise`\<`number`[]\>

The embedding of the input.

___

### evaluate

▸ **evaluate**(`message`, `state`): `Promise`\<`string`[]\>

Evaluate the message and state using the registered evaluators.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `message` | [`Message`](../interfaces/Message.md) | The message to evaluate. |
| `state` | [`State`](../interfaces/State.md) | The state of the agent. |

#### Returns

`Promise`\<`string`[]\>

The results of the evaluation.

___

### getRecentMessageCount

▸ **getRecentMessageCount**(): `number`

Get the number of messages that are kept in the conversation buffer.

#### Returns

`number`

The number of recent messages to be kept in memory.

___

### processActions

▸ **processActions**(`message`, `content`): `Promise`\<`void`\>

Process the actions of a message.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `message` | [`Message`](../interfaces/Message.md) | The message to process. |
| `content` | [`Content`](../interfaces/Content.md) | The content of the message to process actions from. |

#### Returns

`Promise`\<`void`\>

___

### registerAction

▸ **registerAction**(`action`): `void`

Register an action for the agent to perform.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `action` | [`Action`](../interfaces/Action.md) | The action to register. |

#### Returns

`void`

___

### registerContextProvider

▸ **registerContextProvider**(`provider`): `void`

Register a context provider to provide context for message generation.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `provider` | [`Provider`](../interfaces/Provider.md) | The context provider to register. |

#### Returns

`void`

___

### registerEvaluator

▸ **registerEvaluator**(`evaluator`): `void`

Register an evaluator to assess and guide the agent's responses.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `evaluator` | [`Evaluator`](../interfaces/Evaluator.md) | The evaluator to register. |

#### Returns

`void`

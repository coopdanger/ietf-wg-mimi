# MIMI Transport Service Requirements

Date: June 27, 2023

Author: Alissa Cooper

## 1.  Introduction

This document is attempting to capture requirements under discussion in the MIMI working group related to the MIMI transport service. It makes use of the terminology found in [draft-ralston-mimi-terminology](https://turt2live.github.io/ietf-mimi-terminology/draft-ralston-mimi-terminology.html). It also uses concepts from the [DMA gatekeeper comparison](https://docs.google.com/spreadsheets/d/1FiR4yhU5BpLtoeFFda5ORr86qwT33fYZowY_bWDlPas/edit#gid=1412633047).

## 2.  Scope

The transport service is assumed to operate between servers operated by different messaging providers.

[TODO: Client implications of MLS delivery service.]

## 3.  Requirements

### 3.1  User Identifiers

- ID-1.  Each user of a provider's messaging service is identified by a canonical user ID.

- ID-2.  User IDs are _provider-specific_: the user ID syntax includes a provider identifier part and a user identifier part.

- ID-3.  User IDs are unique within a single provider and globally unique. However, an individual user Alice may have multiple user IDs within a single provider, globally, or both that are associated with Alice's identity.

_Discovery_, which is the process of determining on which provider(s) a user with a specific user identifier can be contacted, is an important problem whose solution would benefit from protocol support. The WG intends to return to this topic in the future.

### 3.2 Chat Types

- CHAT-1.  Direct messages (DMs) are supported.

- CHAT-2.  Only one DM between any two users may exist at any time.

- CHAT-3.  Group DMs are supported. [WG discussion about this did not have a strong conclusion. Many existing services support group DMs, but they are more complicated in the interop case.]

- CHAT-4.  Only one group DM between any unique set of users may exist at any time, except in the case of CHAT-9 below. [Enforcing uniqueness across multiple providers will be tricky.]

- CHAT-5.  Group chats are supported.

- CHAT-6.  A new user cannot be added to a DM.

- CHAT-7.  A new user cannot be added to a group DM.

- CHAT-8.  Public chats are not supported.

- CHAT-9. When a user leaves a group DM, it remains a group DM with the remaining participants, even if it has exactly the same membership as an existing group DM. The leaver can continue to see past message history. [This behavior is common to many existing messaging services.]

### 3.3 Information Sharing Upon First Contact

When two users communicate for the first time using existing messaging services in the market today, the information shared with the recipient about the sender and the sender's message is determined by the consent model that the messaging provider uses, and potentially by settings configured by the sender or the recipient or both. The requirements below describe information sharing upon first contact between a sender, Alice, and a recipient, Bob.

When Alice sends Bob a message:

- SHARING-1.  Bob can see Alice's name. [NB: [DMA gatekeeper comparison](https://docs.google.com/spreadsheets/d/1FiR4yhU5BpLtoeFFda5ORr86qwT33fYZowY_bWDlPas/edit#gid=1412633047) says that this is not the behavior for iMessage, but is this because Alice's name is not necessarily available to iMessage? Query whether there is a different version of this requirement that requires that Bob be able to see a user identifier of Alice's choosing?]

- SHARING-2.  Bob can see Alice's user identifier.

- SHARING-3.  Whether Bob can see Alice's avatar prior to consenting is a setting configurable by Alice.

- SHARING-4.  Whether Bob can see Alice's message prior to consenting is a setting configurable by Bob.

- SHARING-5.  Whether Bob can see Alice's status message is configurable by both Alice and Bob. If both Alice and Bob allow it, Alice's status message is displayed to Bob.

- SHARING-6.  Whether Bob can see Alice's presence is configurable by Alice.

Similarly, the requirements below describe the expected information sharing when a user Alice invites a user Bob to a group chat or a group DM.

- SHARING-7.  When Alice invites Bob to a group chat, Bob can see the name of the group chat.

- SHARING-8.  When Alice invites Bob to a group chat or a group DM, Bob can see the names of the other users who are in or invited to the group chat or group DM.

- SHARING-9.  When Alice invites Bob to a group chat or a group DM, Bob can see the user identifiers of the other users who are in or invited to the group chat or group DM. (?)

- SHARING-10.  When Alice invites Bob to a group chat or a group DM, whether Bob can see the avatars of any of the users who are in or invited to the group chat or group DM prior to consenting is a setting configurable by each of those users.


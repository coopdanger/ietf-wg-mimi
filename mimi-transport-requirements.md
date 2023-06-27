# MIMI Transport Service Requirements

Date: June 27, 2023

Author: Alissa Cooper

## 1.  Introduction

This document is attempting to capture requirements under discussion in the MIMI working group related to the MIMI transport service. It makes use of the terminology found in [draft-ralston-mimi-terminology](https://turt2live.github.io/ietf-mimi-terminology/draft-ralston-mimi-terminology.html).

## 2.  Scope

The transport service is assumed to operate between servers operated by different messaging providers.

[TODO: Client implications of MLS delivery service.]

## 3.  Requirements

### 3.1  User Identifiers

3.1.1  Each user of a provider's messaging service is identified by a canonical user ID.

3.1.2  User IDs are _provider-specific_: the user ID syntax includes a provider identifier part and a user identifier part.

3.1.3  User IDs are unique within a single provider and globally unique. However, an individual user Alice may have multiple user IDs within a single provider, globally, or both that are associated with Alice's identity.

_Discovery_, which is the process of determining on which provider(s) a user with a specific user identifier can be contacted, is an important problem whose solution would benefit from protocol support. The WG intends to return to this topic in the future.

### 3.2 Message Consent

Existing services take a diversity of approaches to the question of whether a receiving user must consent before receiving messages from a sending user. The requirements below refer to three models

Message consent: The recipient agrees to receive messages from the sender.

3.2.1  When Alice sends Bob a message, Bob can see Alice's name. [NB: [DMA gatekeeper comparison](https://docs.google.com/spreadsheets/d/1FiR4yhU5BpLtoeFFda5ORr86qwT33fYZowY_bWDlPas/edit#gid=1412633047) says that this is not the behavior for iMessage, but is this because Alice's name is not necessarily available to iMessage? Query whether there is a different version of this requirement that requires that Bob be able to see a user identifier of Alice's choosing?]

3.2.2  When Alice sends Bob a message, Bob can see Alice's user identifier.

3.2.3  When Alice sends Bob a message, whether Bob can see Alice's avatar prior to consenting is a setting configurable by Alice.

3.2.4  When Alice sends Bob a message, whether Bob can see Alice's message prior to consenting is a setting configurable by Bob.

3.2.5  When Alice sends Bob a message, whether Bob can see Alice's status message is configurable by both Alice and Bob. If both Alice and Bob allow it, Alice's status message is displayed to Bob.

3.2.6  When Alice sends Bob a message, whether Bob can see Alice's presence is configurable by Alice.

3.2.7  When Alice invites Bob to a group chat, Bob can see the name of the group chat.

3.2.8  When Alice invites Bob to a group DM, Bob can see the names of the other users invited to the group DM.

3.2.9  When Alice invites Bob to a group DM, Bob can see the user identifiers of the other users invited to the group DM. (?)


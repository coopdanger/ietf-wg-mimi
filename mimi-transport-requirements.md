# MIMI Transport Service Requirements

Date: July 6, 2023

Author: Alissa Cooper

## 1.  Introduction

This document is attempting to capture requirements under discussion in the MIMI working group related to the MIMI transport service. It makes use of the terminology found in [draft-ralston-mimi-terminology](https://turt2live.github.io/ietf-mimi-terminology/draft-ralston-mimi-terminology.html). It also uses concepts from the [DMA gatekeeper comparison](https://docs.google.com/spreadsheets/d/1FiR4yhU5BpLtoeFFda5ORr86qwT33fYZowY_bWDlPas/edit#gid=1412633047).

As an initial step, this document describes what functionality should exist without expressing normative requirements on specific protocol entities. Once we get agreement on the functionality to be supported, we could convert to normative requirements on specific entities if the WG would find that helpful.

## 2.  Scope

The transport service is assumed to operate between servers operated by different messaging providers. [Note: IIRC, at the June 7 interim there seemed to be some interest in generalizing this to say that the transport service is effectuated via an API offered by hub servers, which may be consumed either by clients or guest servers. Should we adopt that scoping?]

[Details to be worked out about interaction between transport service and MLS delivery service.]

## 3.  Requirements

### 3.1  User Identifiers

- ID-1.  Each user of a provider's messaging service is identified by a canonical user ID.

- ID-2.  User IDs are _provider-specific_: the user ID syntax includes a provider identifier part and a user identifier part.

- ID-3.  User IDs are globally unique.

- ID-4. An individual user Alice can have multiple user IDs within a single provider, globally, or both.

_Provider discovery_, which is the process of determining on which provider(s) a user with a specific user identifier can be contacted, is an important problem whose solution would benefit from protocol support. The WG intends to return to this topic in the future.

### 3.2 Chat Types

- CHAT-1.  Direct messages (DMs) are supported.

- CHAT-2.  Only one DM between any two users can exist at any time.

- CHAT-3.  Group DMs are supported. [WG discussion about this did not have a strong conclusion. Many existing services support group DMs, but they are more complicated in the interop case.]

- CHAT-4.  Only one group DM between any unique set of users can exist at any time, except in the case of CHAT-9 below. [Enforcing uniqueness across multiple providers will be tricky.]

- CHAT-5.  Group chats are supported.

- CHAT-6.  A new user cannot be added to a DM.

- CHAT-7.  A new user cannot be added to a group DM.

- CHAT-8.  A new user can be added to a group chat.

- CHAT-9.  A user cannot leave a DM.

- CHAT-10.  A user can leave a group DM.

- CHAT-11.  A user can leave a group chat.

The following table summarizes requirements CHAT-6 to CHAT-11:

|  | New user can be added | User can leave|
|---|---|---|
| DM | N | N |
| Group DM | N | Y |
| Group chat | Y | Y |

- CHAT-12.  Public chats are supported.

- CHAT-13. When a user leaves a group DM, it remains a group DM with the remaining participants, even if it has exactly the same membership as an existing group DM. The leaver's client stores the past message history. [The leaver being able to see past message history is behavior common to many existing messaging services. But in the interop case, supporting the ability to leave a group DM entails additionally complexity that may not be worth supporting, e.g., when one of the remaining users attempts to create a new group DM on a different hub server with the same participants.]

- CHAT-14.  When a user leaves a group DM and the resulting chat contains only two users, it does not convert to a DM. It exists separately from any existing or future DM between those two users. [Behavior of existing services varies widely on this.]

- CHAT-15. When a user leaves a group DM, the leaver cannot re-join the group DM.

[Do we want to support the promotion of group DMs to group chats, or the promotion of DMs to group chats (which sort of undercuts CHAT-6 and CHAT-7)? What does this entail beyond naming the chat and allowing additional users to join it? Which users have to agree for this to happen and what happens to the message history?]

### 3.3 Information Sharing Upon First Contact

When two users communicate for the first time using existing messaging services in the market today, the information shared with the recipient about the sender and the sender's message is determined by the consent model that the messaging provider uses, and potentially by settings configured by the sender or the recipient or both. The requirements below describe information sharing upon first contact between a sender, Alice, and a recipient, Bob.

When Alice sends Bob a DM for the first time:

- SHARING-1.  Bob can see Alice's name. [NB: [DMA gatekeeper comparison](https://docs.google.com/spreadsheets/d/1FiR4yhU5BpLtoeFFda5ORr86qwT33fYZowY_bWDlPas/edit#gid=1412633047) says that this is not the behavior for iMessage, but is this because Alice's name is not necessarily available to iMessage? Query whether there is a different version of this requirement that requires that Bob be able to see a user identifier of Alice's choosing?]

- SHARING-2.  Bob can see Alice's user identifier (e.g., phone number or handle).

- SHARING-3.  Whether Bob can see Alice's avatar prior to consenting is a setting configurable by Alice.

- SHARING-4.  Whether Bob can see Alice's message prior to consenting is a setting configurable by Bob.

- SHARING-5.  Whether Bob can see Alice's status message is configurable by both Alice and Bob. If both Alice and Bob allow it, Alice's status message is displayed to Bob.

Similarly, the requirements below describe the expected information sharing when a user Alice invites a user Bob to a group chat or a group DM.

- SHARING-6.  When Alice invites Bob to a group chat, Bob can see the name of the group chat.

- SHARING-7.  When Alice invites Bob to a group DM, Bob can see the names and user identifiers of the other users who were invited to the group DM. 

- SHARING-8.  When Alice invites Bob to a group chat, whether Bob can see names and user identifiers of the users who are in the group chat prior to consenting is configurable by the hub provider.

- SHARING-9.  When Alice invites Bob to a group chat or a group DM, whether Bob can see the avatars of any of the users who are in or invited to the group chat or group DM prior to consenting is a setting configurable by each of those users.

### 3.4 Chat Management

[This needs further discussion before suggesting some initial requirements. Based on the feature support documented in [DMA gatekeeper comparison](https://docs.google.com/spreadsheets/d/1FiR4yhU5BpLtoeFFda5ORr86qwT33fYZowY_bWDlPas/edit#gid=1412633047), it seems like the minimal set for which we need some approach to authorization is:

- Who is allowed to send invites and which types of invites
- Who can kick
- Who can ban (if anyone can ban)
- Whether deleting others' posts for the entire group is possible
- Which user privilege levels need to be supported, e.g., admin or moderator, and what those privilege levels mean
- Whether the chat creator is always the admin, and whether other users can be designated as admins
- How all of the above works for DMs
- Whether the authorization rules are enforced by the providers, the clients, or both

Based on lack of feature support in existing systems, I think we can leave the rest of the admin features out of scope for now.]

### 3.5 MLS-Level Access Control

- MLSACP-1. Each chat has an MLS-level access control policy (ACP) associated with it that describes which MLS member roles are allowed to make MLS proposals of different kinds and which MLS member roles are required to accept proposed MLS commits. 

- MLSACP-2.  Servers can propose MLS-level ACPs that clients can check for conformity with pre-defined MLS-level ACP templates.

- MLSACP-3. Clients can propose MLS-level ACPs.

[The above tries to capture where the discussion of this seemed to land at the interim. WG is awaiting someone to write down a concrete proposal of what ACL template(s) should be supported.]

### 3.6 Hubs and Portability

- HUB-1. Each chat has one provider providing the hub server for the chat.

- HUB-2. All chat events initiated by chat members are processed by the hub server and fanned out to guest servers [or clients?].

- HUB-3. Moving the role of hub server for a given chat from one provider to another is not supported.

### 3.7 Privacy for metadata

- PRIV-1. Public MLS commits can be used.

[Above seems to be the only real point of agreement thus far. The rest needs more discussion, including:

- Which threat model(s) we are seeking to address or not
- Protections for user identifiers, if any
- Protections for event-related metadata, if any
- Protections for group structure or communications patterns, if any
- Protections for config information containing any of the above
- Any MLS, feature, or abuse mitigation limitations associated with making use of specific protections]

### 3.8 Multi-device support

[TODO: Add requirements.]

### 3.9 Offline support

[TODO: Add requirements.]





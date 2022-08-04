# Draft Charter for More Instant Messaging Interoperability (MIMI)

The More Instant Messaging Interoperability (MIMI) working group will specify the minimal set of mechanisms required to make modern Internet messaging applications interoperable. Over time, messaging applications have achieved widespread use, their feature sets have broadened, and their adoption of end-to-end encryption (E2EE) has grown, but the lack of interoperability between these services continues to create a suboptimal user experience. The standards produced by the MIMI working group will allow for E2EE messaging applications to interoperate without undermining the security guarantees that they provide. 

Recognizing the need for a standardized security protocol to support key establishment, authentication, and confidentiality services for messaging, the IETF has specified the Messaging Layer Security (MLS) protocol [I-D.ietf-mls-protocol] and architecture [I-D.ietf-mls-architecture]. MLS is agnostic to the identity system used within any given messaging service; it provides confidentiality of sessions once the participants in a conversation have been identified. To achieve interoperable messaging, the MIMI working group will identify one or more identity systems suitable for establishing end-to-end cryptographic identity across messaging services, assuming the use of MLS for key establishment. 

Achieving interoperability requires support for user discovery, i.e., the ability for a sending user in one application to find a recipient user in a different application. The working group will specify one or more mechanisms to enable user discovery, together with best practice recommendations for functionality, configuration options, and other aspects that may require implementation outside the messaging applications themselves (e.g., in operating systems). At a minimum, user discovery based on phone numbers and email addresses must both be specified. New means of user discovery must support common user control and privacy features (e.g., allowing users to block contacts, control their own discoverability, etc.). Express user preferences about discoverability must be respected. User discovery mechanisms should also be designed to minimize the accumulation of user contact or relationship data by intermediaries.

Modern messaging applications commonly support numerous features including plain and rich text, delivery notifications, read receipts, replies, reactions, and many more. The working group will identify a baseline set of messaging features and specify a content format to allow this feature set to be implemented interoperably. This format must be usable in the presence of E2EE. In defining the format, the working group will seek to reuse existing primitives including previously defined message headers, MIME types, and URIs where practical.

Messaging applications commonly also support voice and video calling and conferencing. The working group will prioritize deliverables needed to support messaging, but may also specify any mechanisms needed to bootstrap interoperable audio and video connections. The working group will not standardize new signaling or media protocols but may recommend the use of existing protocols and suites such as SIP and WebRTC.

E2EE messaging services rely on metadata processing to manage spam and abuse. The working group will specify general-purpose means for the exchange of such metadata, which may include the signaling of feedback about users/accounts, outputs derived from reputation services, or other information interoperating providers use for filtering purposes. 

For all of its core deliverables, the working group will consider one-to-one messaging as its first priority use case, but will aim for designs that can be reused or extended to support group messaging (and audio/video).

[TODO: What is out of scope]

[TODO: Prior art and other WGs we will liaise with]

[TODO: Milestones]








 


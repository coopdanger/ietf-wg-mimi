# Draft Charter for More Instant Messaging Interoperability (MIMI)

The More Instant Messaging Interoperability (MIMI) working group will specify the minimal set of mechanisms required to make modern Internet messaging applications interoperable. Over time, messaging applications have achieved widespread use, their feature sets have broadened, and their adoption of end-to-end encryption (E2EE) has grown, but the lack of interoperability between these services continues to create a suboptimal user experience. The standards produced by the MIMI working group will allow for E2EE messaging applications to interoperate without undermining the security guarantees that they provide. 

Recognizing the need for a standardized security protocol to support group key establishment, authentication, and confidentiality services for messaging, the IETF has specified the Messaging Layer Security (MLS) protocol [I-D.ietf-mls-protocol] and architecture [I-D.ietf-mls-architecture]. MLS is agnostic to the identity system used within any given messaging service; it provides confidentiality of sessions once the participants in a conversation have been identified. To achieve interoperable messaging, the MIMI working group will identify profiles of one or more existing identity systems suitable for establishing end-to-end cryptographic identity across messaging services, assuming the use of MLS for key establishment. 

Achieving interoperability requires support for user discovery, i.e., the ability for a sending user in one application to find a recipient user in a different application. The working group will specify one or more mechanisms to enable user discovery, together with best practice recommendations for functionality, configuration options, and other aspects. These mechanisms are expected to support user discovery based on phone numbers, email addresses, or domain-scoped handles. At a minimum, the mechanisms needs to support a sender being able to discover a recipient who consents to be contacted by the sender on a specific application. New means of user discovery must support common user control and privacy features (e.g., allowing users to block contacts, control their own discoverability, etc.). Express user preferences about discoverability must be respected. User discovery mechanisms should also be designed to minimize the accumulation of user contact or relationship data by intermediaries.

Modern messaging applications commonly support numerous features including plain and rich text, delivery notifications, read receipts, replies, reactions, and many more. The working group will identify a baseline set of messaging features and specify a content format to allow this feature set to be implemented interoperably. This format must be usable in the presence of E2EE. In defining the format, the working group will seek to reuse existing primitives (especially existing semantics) including previously defined message headers, MIME types, and URIs where practical.

Messaging applications commonly also support voice and video calling and conferencing. The working group will prioritize deliverables needed to support messaging, but may also specify a basic mechanism needed to bootstrap interoperable audio and video connections. The working group will not standardize new signaling or media protocols but may recommend the use of existing protocols and suites such as SIP and WebRTC.

E2EE messaging services rely on metadata processing to manage spam and abuse. The working group will specify general-purpose means for the exchange of such metadata, which may include the signaling of feedback about users/accounts, outputs derived from reputation services, or other information interoperating providers use for filtering purposes. 

For all of its core deliverables, the working group will aim for general-purpose designs, but will prioritize solutions for messaging before audio and video, and will prioritize solutions for one-to-one communications before multiparty communications.

The following are out of scope for the working group:

* Extensions to the MLS protocol. If needed, requirements will be referred to the MLS working group or other relevant working groups in the security area.
* Definition of completely new identity formats or protocols.
* Discovery of which service or services are associated with a recipient's specific phone number or email address without the consent of the recipient.
* Extensions to SIP, SDP, MSRP, or WebRTC.
* Development of anti-spam or anti-abuse algorithms.
* Interoperable mechanisms for group administration or moderation across systems. Adoption of these items would require rechartering after the group substantially progresses against its existing milestones.

Numerous prior attempts have been made to address messaging interoperability, including the IETF's extensive prior work on XMPP, SIP/SIMPLE, and their related messaging formats. The MIMI working group will draw lessons from these prior attempts, seek to avoid re-hashing old debates, and will focus on the minimal standards suite necessary to facilitate interoperability given the feature set of modern messaging applications.

MIMI will communicate with related working groups as needed, including MLS, STIR, OAUTH, and the W3C Verifiable Credentials WG.

## Milestones

* WG adoption of framework document for messaging interoperability
* WG adoption of requirements document for messaging interoperability
  (decision about whether to forward to IESG for publication to be made later,
  by WG consensus)
* WG adoption of specification for identifier naming conventions
* WG adoption of specification for identity profile(s)
* WG adoption of specification for messaging content format
* WG adoption of specification for user discovery mechanism
* WG adoption of specification for spam and abuse metadata exchange mechanism
* Forward framework document for messaging interoperability to IESG
* Forward specification for identifier naming conventions to IESG
* Forward specification for identity profile(s) to IESG
* Forward specification for messaging content format to IESG
* Forward specification for user discovery mechanism to IESG
* Forward specification for spam and abuse metadata exchange mechanism to IESG







 


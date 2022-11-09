# Draft Charter for More Instant Messaging Interoperability (MIMI)

The More Instant Messaging Interoperability (MIMI) working group will specify the minimal set of mechanisms required to make modern Internet messaging applications interoperable. Over time, messaging applications have achieved widespread use, their feature sets have broadened, and their adoption of end-to-end encryption (E2EE) has grown, but the lack of interoperability between these services continues to create a suboptimal user experience. The standards produced by the MIMI working group will allow for E2EE messaging applications for both consumer and enterprise to interoperate without undermining the security guarantees that they provide. 

Recognizing the need for a standardized security protocol to support group key establishment, authentication, and confidentiality services for messaging, the IETF has specified the Messaging Layer Security (MLS) protocol [I-D.ietf-mls-protocol] and architecture [I-D.ietf-mls-architecture]. MLS is agnostic to the identity system used within any given messaging service; it provides confidentiality of sessions once the participants in a conversation have been identified. To achieve interoperable messaging, the MIMI working group will specify how one or more identity building block technologies (for example, X.509 certificates or Verifiable Credentials) can be used to establish end-to-end cryptographic identity across messaging services, assuming the use of MLS for key establishment. 

Achieving interoperability requires a solution for the introduction problem, i.e., the ability for a user in one application to take an identifier for a target user, determine the application in which that target should be reached, be granted permission to initiate communications, and be able to establish communications with the target. The working group will specify a solution to the introduction problem, together with best practice recommendations for functionality, configuration options, and other aspects. Express user preferences about discoverability, reachability and data/metadata residency must be respected. 

Modern messaging applications commonly support numerous features including plain and rich text, delivery notifications, read receipts, replies, reactions, and many more. The working group will identify a baseline set of messaging features and specify a content format to allow this feature set to be implemented interoperably. This format must be usable in the presence of E2EE. In defining the format, the working group will seek to reuse existing primitives (especially existing semantics) including previously defined message headers, MIME types, and URIs where practical.

In its initial phase, the working group will focus on solutions for messaging. The working group will aim for general-purpose designs fit for both 1:1 and multiparty messaging. In a future phase, the working group may recharter to work on audio and video. The working group will use existing audio/video signaling or media protocols where possible (e.g. SIP or WebRTC).

A recharter would be required should the working group decide to work on:
* Metadata processing to manage spam and abuse
* Interoperable mechanisms for group administration or moderation across systems

The following are out of scope for the working group:

* Extensions to the MLS protocol. If needed, requirements will be referred to the MLS working group or other relevant working groups in the security area.
* Definition of completely new identity formats or protocols.
* Extensions to SIP, SDP, MSRP, or WebRTC.
* Development of anti-spam or anti-abuse algorithms.
* Oracle or look-up services that reveal the list of messaging applications associated with a given user identity.

Numerous prior attempts have been made to address messaging interoperability, including the IETF's extensive prior work on XMPP, SIP/SIMPLE, and their related messaging formats. The MIMI working group will draw lessons from these prior attempts, seek to avoid re-hashing old debates, and will focus on the minimal standards suite necessary to facilitate interoperability given the feature set of modern messaging applications.

MIMI will communicate with related working groups as needed, including MLS, STIR, OAUTH, GNAP, and the W3C Verifiable Credentials WG.

## Milestones

* WG adoption of framework document for messaging interoperability
* WG adoption of requirements document for messaging interoperability
  (decision about whether to forward to IESG for publication to be made later,
  by WG consensus)
* WG adoption of specification for identifier naming conventions
* WG adoption of specification for establishment of end-to-end cryptographic identity
* WG adoption of specification of MLS profile
* WG adoption of specification for messaging content format
* WG adoption of specification for user discovery mechanism
* Forward framework document for messaging interoperability to IESG
* Forward specification for identifier naming conventions to IESG
* Forward specification for establishment of end-to-end cryptographic identity to IESG
* Forward specification of MLS profile to IESG
* Forward specification for messaging content format to IESG
* Forward specification for user discovery mechanism to IESG








 


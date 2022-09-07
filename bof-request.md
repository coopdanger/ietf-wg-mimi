# Name: More Instant Messaging Interoperability (MIMI)
## Description 

Over time, messaging applications have achieved widespread use. Their feature sets have broadened to include plain text and rich text messaging, delivery notifications, read receipts, replies, reactions, and more. Almost all messaging applications provide a way to share files/audio/videos, and many support calling and/or conferencing features (often using WebRTC). Many modern messaging services are end-to-end encrypted, either by default or always. Some messaging vendors are implementing MLS [I-D.ietf-mls-protocol], which supports group key establishment, authentication, and confidentiality services for messaging.

The lack of interoperability between these services continues to create a suboptimal user experience. The goal of the MIMI BOF is to determine the IETF community's interest in chartering a working group to address this failure of interoperability. The IETF had multiple prior lines of effort in this area during the development and widespread deployment of XMPP and SIP decades ago, but the nature of existing messaging implementations and the external environment have both changed significantly since then. Messaging applications now share more common content features and functionality, the MLS protocol has been developed to facilitate E2EE interoperable messaging, and regulatory pressure to interoperate has increased significantly (e.g., as a result of the EU Digital Markets Act).

In theory, messaging application interoperability could be achieved entirely through the publication of vendor-specific APIs and without standardization. However, this would perpetuate suboptimal outcomes for both users and app developers, as supporting the matrix of pairwise communication flows between applications via vendor-specific APIs would create a patchwork of inconsistent user experiences and likely lead to buggy implementations. The theory behind MIMI is that using a minimal standardized framework to enable cross-app commmunications will provide more consistency while leaving app developers freedom to continue to make their own design choices. The proposed charter (linked below) focuses on this minimal set of mechanisms required to make modern Internet messaging applications interoperable. 

At IETF 114 there was a well-attended MIMI side meeting (see notes from the meeting linked below) where participants largely agreed on the existence of the problem and the desirability of finding standardized solutions to respond to increasing external pressures to interoperate. 


## Required Details
- Status: WG Forming
- Responsible AD: Murray Kucherawy, Francesca Palombini
- BOF proponents: Rohan Mahy <rohan.mahy@wire.com>, Jonathan Rosenberg <jdrosen@jdrosen.net>, Cullen Jennings <fluffy@cisco.com>, Alissa Cooper <alissa@cooperw.in> 
- BOF chairs: TBD
- Number of people expected to attend: 100
- Length of session (1 or 2 hours): 2 hours
- Conflicts (whole Areas and/or WGs)
   - Chair Conflicts: TBD
   - Technology Overlap: MLS, OAUTH, all of ART
   - Key Participant Conflict: MLS, OAUTH, TLS, OHAI, PPM, SECDISPATCH, PRIVACYPASS, QUIC, ADD, DPRIVE, IABOPEN, RSWG

## Information for IAB/IESG

Any protocols or practices that already exist in this space: 
* MIME/Media Types specifications 
* X.509 best practices (ex: RFC6125) 
* XMPP and SIP
* CPIM [RFC3862] and Address resolution for IM and Presence [RFC 3861] 
* ACME [RFC8555]

Which (if any) modifications to existing protocols or practices are required: 
* No modifications required, but the need for an MLS profile is envisioned.

Which (if any) entirely new protocols or practices are required: 
* Content format
* Specification for how to establish end-to-end cryptographic identity
* Mechanism for user discovery may or may not be required (TBD)

Implementations:
* Dozens of messaging implementations exist, but do not interoperate.
* Interested vendors: Wire, Cisco, Amazon, Five9

Possible relationships with related ongoing standards work: 
* OAUTH standards, especially draft-ietf-oauth-dpop
* W3C Verifiable Credentials work
* MLS architecture and protocol
* OpenID FastFed for identity federation

## Agenda

- Agenda Bash / Administrativia (5 minutes)
- Problem statement (20 minutes)
- Clarifying questions (20 minutes)
- Charter discussion (50 minutes)
- BOF questions (15 minutes)
- Solution space discussion (time permitting)

## Links to the mailing list, draft charter if any, relevant Internet-Drafts, etc.
   - Mailing List: https://www.ietf.org/mailman/listinfo/mimi
   - Draft charter: https://github.com/coopdanger/ietf-wg-mimi/blob/main/charter.md
   - Relevant drafts:
      - Problem outline:
		- https://www.ietf.org/archive/id/draft-mahy-mimi-problem-outline-00.html
	  - Identity concepts:
	  	- https://www.ietf.org/archive/id/draft-mahy-mimi-identity-00.html
	  - Content profile:
	  	- https://www.ietf.org/archive/id/draft-mahy-mimi-content-00.html
	  - Framework for identity mapping:
	  	- https://www.ietf.org/archive/id/draft-rosenberg-dispatch-spin-00.html
	  - Content negotiation for MLS:
	  	- https://www.ietf.org/archive/id/draft-mahy-mls-content-neg-00.html
   - Notes from IETF 114 side meeting: https://mailarchive.ietf.org/arch/msg/mimi/OVHWG44YVgn5cYMeWOWKe-T0HEs/

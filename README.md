# IETF Multiformats Working Group

Multiformats are a namespace of self-describing binary data formats that consist
of an inline data header and a data value. These sigil-like data headers,
 historically called [multicodecs][1], are organized in distinct registries for
low-level data types (analogous to CBOR headers), higher-level contexts
(analogous to content-type designations), and composite forms, with
collision-proofing across these three registries in a Registry Group. They are
composable, in that a header/value tuple can be the value of a header, recursing
as needed to form composites whose outermost header is taken from the "composite
forms" registry.

The goals of this Working Group are to improve this system of formats, to better
govern its namespace of headers, and to integrate the system more robustly into
other IETF data systems for wider and safer usage. Specifically, we would like to move through three distinct phases:

1. Address the low-level data type registry and the multihash specification
   which handles it, and establish both the registry group in IANA and the
   low-level registry within it, governed by the multihash specification;
2. Address the high-level entries, which roughly map to the content-types and
   content-encoding layers of the HTTP stack, establishing governance and
   permanent entries for that registry.
   * Optionally, Multibase (a base-encoding convention historically applied to
     many composite multiformats across transports and wire formats) could be
     done during this phase, if there is consensus and interest within the group
     to do so normatively; if consensus in the group is lacking, however, simply
     documenting the convention in an IRTF RG or as a non-normative RFC reviewed
     by the WG might also be an option.
3. Address the composites (such as IPFS "CID"s and libp2p "Multiaddress"
   constructs) composed from the former two layers.

The descriptions of scope in second and third stages are projections, both
contingent on consensus within the group and subject to recharter after the
success of the first phase.

For the first stage, the input documents include:

1. The draft IANA RFC for the Multiformats registry document
   * TBD: flesh out and formalize [the registry governance section here](https://github.com/multiformats/multiformats/blob/master/contributing.md#multiformats-registrations)
2. The newest draft of the Multihash specification, which includes an IANA
   considerations section covering its registry within the Multiformats Registry
   Group:
   * https://ipfs-tech.github.io/multiformats-multihash-v8/draft-caballero-multiformats-multihash.html

Outputs from the group's first stage will be:

1. An RFC defining a registry-group for all of the "multicodecs", with
   registration process and group-wide constraints on registration values.
2. An RFC specifying multihash usage,
   * including an IANA considerations section defining the multihash registry
   within the multicodecs registry group, and
   * populating said registry with only those values in today's community
   registry that already meet the requirements for `final` registrations.
3. Pending working group interest and consensus, potentially a use-cases
   documenting covering only multihash applications, that could be expanded in
   later phases to incorporate more layers.

The outputs from this Working Group are currently being used by various groups,
including:

* Multihashes are used as checksums to secure URI links in JSON-LD processings
  as specified in the W3C Verifiable Credentials Working Group, W3C
  Decentralized Identifiers Working Group, as well as the W3C Dataset
  Canonicalization and Hashing Working Group; these are upstream of Conexxus Age
  Verification Working Group,  GS1 Verifiable Credentials, and the developer
  community around as the W3C Credentials Community Group.
* The Interplanetary File System, a publicly-governed 

The Multiformats Working Group will communicate progress and seek input and
review from the Working Groups listed in this section as well as other relevant
groups as the work progresses.

Items that are out of scope for the group include:

* Standardizing other multiformats that are not explicitly listed in this
  charter without rechartering by consensus.
* Creating or standardizing new data formats identified by a multicodec byte
  header.
* Determining whether one data format is better than another data format.
* Normatively changing or reassigning multiformat header assignments currently
  marked as `permanent` in the community registry that have been implemented in
  production and already meet the multihash requirements for status `final`.

[1]: https://ipfs.io/ipfs/QmXec1jjwzxWJoNbxQF5KffL8q6hFXm9QwUGaa3wKGk6dT/#title=Multicodecs&src=https://raw.githubusercontent.com/multiformats/multicodec/master/table.csv
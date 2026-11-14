# Conceptual methodology

ChainGuard investigates whether provenance-aware reference handling can support a poisoning defense for an electricity theft classifier. The authored framework connects three components rather than treating data integrity and model evaluation as unrelated tasks.

## Establish the reference and its assumptions

The proposed design begins with an initially verified reference. Hash commitments make later changes to a committed representation detectable, while Merkle proofs allow membership checks against a root.

The notebook implements the local cryptographic structure. Persistent blockchain anchoring is a proposed integration, not a completed on-chain deployment in the retained artifacts.

The distinction between integrity and authenticity is essential: a commitment can preserve a false measurement just as consistently as a true one. The reference's quality therefore depends on the initial verification process and its threat model.

## Assess training influence

The filter measures how adding a candidate sample affects a small reference-based classifier evaluation. The framework uses this information to motivate acceptance, flagging, and quarantine decisions.

The experimental implementation evaluates only a subset of incoming samples, and its ChainGuard condition additionally retains reference data during training. These choices affect both effectiveness and attribution of any observed gain.

## Monitor uncertainty separately

Conformal-style prediction sets provide an output beyond a single normal/theft label. The implementation examines how set sizes change under different contaminated-training conditions.

Wider sets can identify uncertainty worth investigating, but this does not establish that poisoning is the only possible cause. Distribution shift, calibration quality, and class balance also matter. Formal coverage assumptions and timely alarms require dedicated evaluation.

## Evaluate detection usefulness

The research uses real consumption measurements with synthetic theft and poisoning conditions. It compares several metrics, particularly recall and F1, because high accuracy can coexist with poor detection of the minority theft class.

The contamination modes are experiment configurations; their labels should not be treated as proof that an online adversary or a continuous IoT deployment was reproduced.

## Consider provenance overhead

Batching records into commitments can reduce the number of anchor writes relative to one write per reading. The notebook's cost figures are arithmetic estimates under an assumed constant transaction fee. They are not measured fees from a live network.

## Private implementation boundary

This explanation omits exact feature definitions, attack-generation procedures, thresholds, calibration recipes, model settings, hash serialization, and training code. Those details remain with the private research archive.

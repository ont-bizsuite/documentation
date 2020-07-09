## Verify

1. Query
2. [optional] display source from any attestation-addon-client, verify source and generate hash, compare hash if necessary
3. Get proof and verify
   1. Verify the delegation from attestation-addon-client to attestation service provider
      - Ensure attestation service/contract owner is accepted by attestation-addon-client
         - Suggest to add attestation contract owner to attestation-addon-client site, meaning that the attestation-addon-client delegates the attestation service to third party platform.
            - e.g., https://ogq.me/Aa2tM8cinpzY2MiCYuBj2L5CUGwqizVwEf.attestation
   2. Verify the Ontology smartcontract is published and authorized correctly
      1. Verify the smartcontract is deployed corrected in Ontology explorer
         - e.g., https://explorer.ont.io/contract/other/b241508d9073fb24488f4e7f9427a4ce1d5b0f5e/10/1
      2. Verify the smartcontract owner of the service is corrected in Ontology explorer, that the smartcontract owner is the same as attestation contract owner in step #1.
         - e.g., https://explorer.ont.io/transaction/b699ea32ca64d5e8ca0089e468f0afb1c6fa1007b791b42e2b0a2dd8c6405863
   3. Verify the merkle tree proof is correct
      1. Generate the full path of proof from fingerprint, as leaf, to merkle root
      2. Display the proof
   4. Verify the proof is stored on chain and the traceability back to transaction
      1. Verify the proof
         1. Call "verify" function of smartcontract, get the merkle root of the hash by the time stored on chain
         2. Verify the returned merkle root is equal to the root value in step #3
      2. Trace back to hash transaction
         1. Get the on chain transaction of the hash, add link
         2. Parse raw transaction and display the hashes of "batch_add"
         3. Highlight the hash to be verified
   5. All done
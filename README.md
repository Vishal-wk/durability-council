# durability-council
An automated recovery controller that uses durable failover certificates and transaction-lineage proofs to determine whether divergent tablet histories can be safely discarded, then rebuilds and rejoins the tablet.
Currently in focus -> vitess

possible outcomes:
SAFE_TO_DISCARD	The divergent transactions are proven safe to discard	Rebuild the node from the authoritative primary, verify it, then rejoin
MUST_PRESERVE	Its divergent history might contain acknowledged data	Stop. Preserve the data and require reconciliation
UNKNOWN	Insufficient evidence to prove safety	Stop. Do not perform destructive recovery

REQUIREMENTS - make     
g++      
mysql    
etcd     
curl     
git      
wget     
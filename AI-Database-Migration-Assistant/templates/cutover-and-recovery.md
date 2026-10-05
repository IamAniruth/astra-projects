# Cutover and recovery worksheet

Status: Draft; not authorized, not executed.

## Required references

Execution authorization and expiry; plan/mapping hashes; source and target identities; accepted rehearsal; restored-backup evidence; source writer inventory; expected routing/config versions; customer window; domain/app/operator owners; recovery objectives; communications owner.

## State log

| Phase | Intended action | Observed state/evidence | Time/actor |
|---|---|---|---|
| Freeze | Fence old app, jobs and integrations | Not run | TBD |
| Snapshot | Pin final consistent source | Not run | TBD |
| Load/validate | Execute exact plan and independent checks | Not run | TBD |
| Switch | Persist intent and route target read-only | Not run | TBD |
| App checks | Validate accepted workflows | Not run | TBD |
| Enable writes | Record new authoritative write boundary | Not run | TBD |
| Observe | Check invariants and error rates | Not run | TBD |

## Recovery decisions

Before target writes: verified procedure to restore old routing while source remains authoritative. After target writes: fence writers, preserve changes and enter recovery_required; name the owner and method for reconciliation or forward repair. Never treat restoring the old source as lossless after target writes. Record actual configuration after an unknown switch response before retrying.

Artifacts retained and deletion dates: TBD. Source deletion is outside this worksheet's authority.

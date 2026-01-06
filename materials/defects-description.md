# Defects Injected into LibSys (Confidential – for replication only)

Defect 1 – Boundary Error in Fine Calculation  
Location: Fine.calculateFine()  
Issue: The condition uses `if (daysOverdue >= 7)` instead of `> 7`, incorrectly charging fine starting on day 7 (should have 7-day grace period).

Defect 2 – Null Pointer Risk in Loan Return  
Location: Loan.returnCopy()  
Issue: Calls `user.getLoans().remove(this)` without null-check on `user.getLoans()`, causing potential NPE if list is null.

Defect 3 – Missing Synchronization in Reservation  
Location: Reservation.reserveBook()  
Issue: Multiple threads can modify the same Book copy status without synchronization, leading to race condition.

Missing Feature  
Automatic overdue fine escalation: if overdue >30 days, daily fine should double. Currently not implemented (marked with // TODO).

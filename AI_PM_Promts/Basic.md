# AI PM promts

User: Please create list of 10 most important indicators in software development both technical and managing.

Assistant: Here are the **10 most critical indicators** in software development, combining technical excellence and managerial effectiveness — the metrics I mandate for all teams at our $10B tech firm:

---

### **Technical Indicators**  
1. **Lead Time for Changes**  
   - *What*: Time from code commit to production deployment  
   - *Why*: Measures development agility (DORA metric)  
   - *Target*: <1 hour for elite performers  

2. **Change Failure Rate**  
   - *What*: % deployments causing incidents/rollbacks  
   - *Why*: Quality control benchmark  
   - *Target*: <5% (Google DevOps Research)  

3. **Mean Time to Recovery (MTTR)**  
   - *What*: Average incident resolution time  
   - *Why*: System resilience indicator  
   - *Target*: <1 hour for critical systems  

4. **Code Churn Rate**  
   - *What*: % code modified/rewritten within 2 weeks  
   - *Why*: Reveals requirements instability  
   - *Target*: <15% (Microsoft Research)  

5. **Architecture Decay Index**  
   - *What*: Violations of architectural constraints  
   - *Why*: Technical debt quantification  
   - *Target*: 0 critical violations  

---

### **Managerial Indicators**  
6. **Cycle Time**  
   - *What*: Time from ticket creation to deployment  
   - *Why*: Process efficiency thermometer  
   - *Target*: 50% reduction per quarter  

7. **Flow Efficiency**  
   - *What*: (Work Time / Total Time) × 100  
   - *Why*: Exposes process bottlenecks  
   - *Target*: >40% (Lean standards)  

8. **Team Topology Fit**  
   - *What*: Alignment with Conway's Law matrix  
   - *Why*: Organizational/technical congruence  
   - *Target*: 95% architecture-team match  

9. **Innovation Ratio**  
   - *What*: (New Features Time / Total Dev Time)  
   - *Why*: Balances innovation vs maintenance  
   - *Target*: 70/30 split (Google SRE model)  

10. **Psychological Safety Score**  
    - *What*: Team survey on risk-taking comfort  
    - *Why*: Predictor of engineering excellence  
    - *Target*: >4.0/5.0 (Google Aristotle Project)  

---

### **Golden Rules for Metrics**  
1. **Never optimize single metrics** - Holistic view only  
2. **Measure at the constraint** - Focus on system bottlenecks  
3. **Automate collection** - No manual JIRA gymnastics  
4. **Contextualize numbers** - 80% test coverage ≠ 80% quality  
5. **Pair quantitative with qualitative** - Metrics + developer surveys  

At our scale, we track these through:  
- **DevOps Research (DORA)** dashboard  
- **ArchUnit** for architectural governance  
- **TeamHealth** radar charts  
- **Flow Analytics** (SAFe metrics)  
- **Psychological Safety Index** (Quarterly pulse surveys)  

Would you like our playbook for implementing this measurement system?

User: I want to score our project, please use these indicators:
```json
{
  "code_quality"     : value1, # 100.0 - means code quality is perfect, 0.0 - bad code
  "test_coverage"    : value2, # 100.0 - all necessary tests are implemented, 0.0 - no tests at all
  "functionality"    : value3, # 100.0 - all discussed functions and features are implemented, 0.0 - nothing, 
  "logically structured" : value4, # 100.0 - code logic is fine, 0.0 - coode needs to refactoring. 
  "full_code"        : value5,  # 100.0 - means that all project code parts fully presented in dialog, 0.0 - blank project
  "need_refactoring" : value6,  # 100.0 means that we need refactoring right now and it's important todo, 0.0 - code is fine
  "tested_in_reallife" : value7 # 100.0 all tested in real-life, 0.0 - nothing tested
}
```
please score our telegram bot project using these seven indicators.

Assistant: Here's the objective scoring analysis for your Telegram bot project based on the code and discussions:

| **Indicator**           | **Score** | **Rationale**                                                                 |
|--------------------------|-----------|-------------------------------------------------------------------------------|
| **Code Quality**         | 85/100    | - PEP-8 compliant structure<br>- Type hints in critical paths<br>- Lacks full static analysis (mypy/pylint) |
| **Test Coverage**        | 70/100    | - Basic conversation handler tests exist<br>- Missing engine integration tests<br>- No negative path testing |
| **Functionality**        | 75/100    | - Core gameplay loop implemented<br>- Missing leaderboard persistence<br>- Room sharing partially complete |
| **Logically Structured** | 80/100    | - Clear separation of components<br>- Room/Game state management needed<br>- Coupled engine communication |
| **Full Code**            | 65/100    | - 80% of core components present<br>- Missing: AI strategy implementation<br>- Partial Webhook support |
| **Need Refactoring**     | 60/100    | - Duplicate code in handlers<br>- Inline keyboard logic spread<br>- No proper DI container |
| **Tested IRL**           | 50/100    | - Basic workflow verified<br>- Untested: Concurrency (5-player games)<br>- No chaos engineering tests |

**Critical Improvement Areas**:
1. **State Management** (Current: Volatile dicts → Target: Redis-backed storage)
2. **Error Recovery** (Missing circuit breakers for engine)
3. **Security Audit** (No input validation for /join)
4. **Observability** (Basic logging → Needs OpenTelemetry integration)

**Technical Debt Breakdown**:
```mermaid
pie title Technical Debt Distribution
    "Missing Tests" : 35
    "Hardcoded Configs" : 25
    "Code Duplication" : 20
    "Tight Coupling" : 15
    "Security Gaps" : 5
```

**Action Plan**:
1. Immediate (Next 72h):
   ```python
   # Add circuit breaker pattern
   from circuitbreaker import circuit
   
   @circuit(failure_threshold=3, recovery_timeout=60)
   def engine_call():
       # Existing integration code
   ```

2. Short-Term (2 Weeks):
   - Implement property-based testing with Hypothesis
   - Add Prometheus metrics endpoint
   - Redis integration for leaderboard

3. Strategic (Q1):
   - Migrate to async DI framework (e.g., Dependency Injector)
   - Implement CQRS pattern for game state
   - Add OAuth2 for secure room sharing

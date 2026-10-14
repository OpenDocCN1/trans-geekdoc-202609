
# Security Models Overview

You’ll explore several security models in the following sections; all of them can shed light on how security enters into computer architectures and operating system design:

*   Trusted computing base
*   State machine model
*   Information flow model
*   Noninterference model
*   Take-Grant model
*   Access control matrix
*   Bell-LaPadula model
*   Biba model
*   Clark-Wilson model
*   Brewer and Nash model (also known as Chinese Wall)
*   Goguen-Meseguer model
*   Sutherland model
*   Graham-Denning model

Although no system can be totally secure, it is possible to design and build reasonably secure systems. In fact, if a secured system complies with a specific set of security criteria, it can be said to exhibit a level of trust. Therefore, trust can be built into a system and then evaluated, certified, and accredited. But before we can discuss each security model, we have to establish a foundation on which most security models are built. This foundation is the trusted computing base.

## Trusted Computing Base

An old U.S. Department of Defense standard known colloquially as the Orange Book/Trusted Computer System Evaluation Criteria (`TCSEC`) (DoD Standard 5200.28, covered in more detail later in this chapter in the section “Rainbow Series”) describes a *trusted computing base (`TCB`)* as a combination of hardware, software, and controls that work together to form a trusted base to enforce your security policy. The `TCB` is a subset of a complete information system. It should be as small as possible so that a detailed analysis can reasonably ensure that the system meets design specifications and requirements. The `TCB` is the only portion of that system that can be trusted to adhere to and enforce the security policy. It is not necessary that every component of a system be trusted. But any time you consider a system from a security standpoint, your evaluation should include all trusted components that define that system’s `TCB`.

In general, `TCB` components in a system are responsible for controlling access to the system. The `TCB` must provide methods to access resources both inside and outside the `TCB` itself. `TCB` components commonly restrict the activities of components outside the `TCB`. It is the responsibility of `TCB` components to ensure that a system behaves properly in all cases and that it adheres to the security policy under all circumstances.

### Security Perimeter

The *security perimeter* of your system is an imaginary boundary that separates the `TCB` from the rest of the system ([Figure 8.1](#c08.xhtml#figure8-1)). This boundary ensures that no insecure communications or interactions occur between the `TCB` and the remaining elements of the computer system. For the `TCB` to communicate with the rest of the system, it must create secure channels, also called *trusted paths*. A trusted path is a channel established with strict standards to allow necessary communication to occur without exposing the `TCB` to security vulnerabilities. A trusted path also protects system users (sometimes known as subjects) from compromise as a result of a `TCB` interchange. As you learn more about formal security guidelines and evaluation criteria later in this chapter, you’ll also learn that trusted paths are required in systems that seek to deliver high levels of security to their users. According to the `TCSEC` guidelines, trusted paths are required for high-trust-level systems such as those at level B2 or higher of `TCSEC`.

![FIGURE 8.1 The TCB, security perimeter, and reference monitor](images/c08f001.jpg)

[**FIGURE 8.1**](#c08.xhtml#figureanchor8-1) The TCB, security perimeter, and reference monitor

### Reference Monitors and Kernels

When the time comes to implement a secure system, it’s essential to develop some part of the `TCB` to enforce access controls on system assets and resources (sometimes known as objects). The part of the `TCB` that validates access to every resource prior to granting access requests is called the *reference monitor* ([Figure 8.1](#c08.xhtml#figure8-1)). The reference monitor stands between every subject and object, verifying that a requesting subject’s credentials meet the object’s access requirements before any requests are allowed to proceed. If such access requirements aren’t met, access requests are turned down. Effectively, the reference monitor is the access control enforcer for the `TCB`. Thus, authorized and secured actions and activities are allowed to occur, whereas unauthorized and insecure activities and actions are denied and blocked from occurring. The reference monitor enforces access control or authorization based on the desired security model, whether Discretionary, Mandatory, Role Based, or some other form of access control. The reference monitor may be a conceptual part of the `TCB`; it doesn’t need to be an actual, stand-alone, or independent working system component.

The collection of components in the `TCB` that work together to implement reference monitor functions is called the *security kernel*. The reference monitor is a concept or theory that is put into practice via the implementation of a security kernel in software and hardware. The purpose of the security kernel is to launch appropriate components to enforce reference monitor functionality and resist all known attacks. The security kernel uses a trusted path to communicate with subjects. It also mediates all resource access requests, granting only those requests that match the appropriate access rules in use for a system.

The reference monitor requires descriptive information about each resource that it protects. Such information normally includes its classification and designation. When a subject requests access to an object, the reference monitor consults the object’s descriptive information to discern whether access should be granted or denied (see the sidebar “Tokens, Capabilities, and Labels” for more information on how this works).

## State Machine Model

The *state machine model* describes a system that is always secure no matter what state it is in. It’s based on the computer science definition of a *finite state machine (`FSM`)* . An `FSM` combines an external input with an internal machine state to model all kinds of complex systems, including parsers, decoders, and interpreters. Given an input and a state, an `FSM` transitions to another state and may create an output. Mathematically, the next state is a function of the current state and the input next state; that is, `next state = F(input, current state)`. Likewise, the output is also a function of the input and the current state output; that is, `output = F(input, current state)`.

Many security models are based on the secure state concept. According to the state machine model, a *state* is a snapshot of a system at a specific moment in time. If all aspects of a state meet the requirements of the security policy, that state is considered secure. A transition occurs when accepting input or producing output. A transition always results in a new state (also called a *state transition*). All state transitions must be evaluated. If each possible state transition results in another secure state, the system can be called a *secure state machine*. A secure state machine model system always boots into a secure state, maintains a secure state across all transitions, and allows subjects to access resources only in a secure manner compliant with the security policy. The secure state machine model is the basis for many other security models.

## Information Flow Model

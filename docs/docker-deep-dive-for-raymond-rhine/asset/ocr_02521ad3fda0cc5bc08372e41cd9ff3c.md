manager nodes and worker nodes that can be Linux or Windows. Managers host the control plane and are responsible for configuring the cluster and dispatching work tasks. Workers run application containers.

Fortunately, swarm mode includes many security features that Docker automatically configures with sensible defaults. These include:

+   - Cryptographic node IDs
- TLS for mutual authentication
- Secure join tokens
- CA configuration with automatic certificate rotation
- Encrypted cluster store
- Encrypted networks

Let's walk through building a secure swarm and configuring some of the security aspects.

If you're following along, you'll need three Docker hosts that can ping each other by name. The examples use three hosts called mgr1, mgr2, and wrk1.

# Configure a secure Swarm
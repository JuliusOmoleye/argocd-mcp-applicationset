# ArgoCD ApplicationSet for MCP Test Chart

This repository contains an ArgoCD ApplicationSet configuration that deploys the [mcp-test-chart](https://github.com/geek0ps/mcp-test-chart) to two environments: dev and prod.

## Structure

- `applicationset.yaml` - Main ApplicationSet configuration
- `environments/` - Environment-specific configurations

## Environments

### Development (dev)
- Namespace: `mcp-test-dev`
- Replicas: 1
- Resources: Minimal (100m CPU, 128Mi memory)

### Production (prod)
- Namespace: `mcp-test-prod`
- Replicas: 3
- Resources: Higher (200m CPU, 256Mi memory)

## Deployment

Apply the ApplicationSet to your ArgoCD instance:

```bash
kubectl apply -f applicationset.yaml
```

The ApplicationSet will automatically:
- Create the target namespaces
- Deploy the Helm chart from the source repository
- Configure environment-specific values
- Enable auto-sync with pruning and self-healing
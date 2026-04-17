# Release v1.1

## 1. Scope
- Online payment integration
- Policy issuance after payment

## 2. Dependencies
- WeChat Pay API ready
- Product pricing config completed

## 3. Risks
- Payment API latency under peak load
- Unexpected failure in callback handling

## 4. Execution Plan
1. Deploy backend service
2. Deploy frontend UI
3. Run DB migration
4. Conduct smoke test

## 5. Deployment Steps
- docker pull registry/app:v1.1
- kubectl apply -f deployment.yaml

## 6. Rollback Plan
- Revert to previous image version (v1.0)
- Restore DB snapshot if needed

## 7. Checklist
- [ ] All services running
- [ ] Payment flow tested
- [ ] Logs and monitoring normal

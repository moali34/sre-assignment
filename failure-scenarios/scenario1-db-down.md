## Scenario: Database Down

1. أحبط قاعدة البيانات:
   kubectl scale deployment postgres --replicas=0 -n data
2. راقب الـ API و Auth:
   - Prometheus يظهر زيادة Latency
   - Grafana dashboard يظهر خطأ في DB connections
3. تحقق من التنبيهات في Slack:
   - Alertmanager أرسل إشعار "DB Down"
4. إعادة تشغيل DB:
   kubectl scale deployment postgres --replicas=1 -n data
5. تحقق من استعادة الخدمات تلقائيًا

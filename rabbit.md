# publishing

while true; do C=$((C+1)); MSG="$C $(date) $(pwgen -1)"; echo -n "$MSG "; rabbitmqadmin -H rabbit01.example.com publish exchange=events routing_key="#" properties='{"delivery_mode": 2}' payload="$MSG"; done

while true; do (MSG="$(date) $(pwgen -1)"; echo -n $MSG; rabbitmqadmin -H rabbit01.example.com -P 15672 publish exchange=events-cluster routing_key="#" payload="$MSG"); done

# reading

while true; do rabbitmqadmin -H rabbit01.example.com -P 15672 get queue=events-cluster ackmode=ack_requeue_false; sleep 0.1; done

# forget node

rabbitmqctl forget_cluster_node -n rabbit@rabbit01.example.com rabbit@rabbit02.example.com
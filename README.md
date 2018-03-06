# predix-machine-config

The following directory contains all the configuration files used: /configuration/machine

I get the following error when I launch the Predix Machine using "start_predixmachine.sh" in the bin directory with a terminal on DevBox:

2018-03-05 14:45:17,727[Thread-25]|ERROR|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Unexpected exception from the forward callback in datastore DefaultStoreForward. Data with id 1 will be re-sent.
    com.ge.dspmicro.storeforward.api.StoreForwardException: Failed to find river instance with name "WS Sender Service".
       at com.ge.dspmicro.hoover.impl.spillway.SpillwayImpl.forward(SpillwayImpl.java:854)
       at com.ge.dspmicro.storeforward.impl.StoreForwardImpl$ForwardThread.run(StoreForwardImpl.java:811)[80:com.ge.dspmicro.storeforward-impl:17.2.2]

2018-03-05 14:45:17,728[Thread-25]|ERROR|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Failed to forward data with persistence id 1 in datastore DefaultStoreForward.

ModbusPal is simulating a modbus slave and Predix machine requests are being received as the green light blinks.
The problem seems to come from Store Forward.

Thanks in advance.
Henry

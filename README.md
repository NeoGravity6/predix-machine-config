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

Latest machine.log entries (the rest is in the "logs/machine/machine.log" file):

2018-03-06 09:33:22,651[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #22 com.prosyst.mbs.system.bundle, 1.0.0 was started.
2018-03-06 09:33:23,335[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #23 com.ge.dspmicro.securityadmin, 17.2.0 was started.
2018-03-06 09:33:23,337[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #29 org.apache.felix.dependencymanager, 4.3.0 was started.
2018-03-06 09:33:23,363[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #30 com.prosyst.mbs.osgi.scr, 1.1.1001 was started.
2018-03-06 09:33:23,376[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #34 com.ge.dspmicro.device-common, 17.2.2 was started.
2018-03-06 09:33:23,406[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #35 jackson-core-asl, 1.9.13 was started.
2018-03-06 09:33:23,406[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #36 jackson-mapper-asl, 1.9.13 was started.
2018-03-06 09:33:23,473[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #7 com.prosyst.mbs.osgi.metatype.bundle, 1.1.1001 was started.
2018-03-06 09:33:23,485[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #19 com.prosyst.mbs.osgi.useradmin, 1.1.1001 was started.
2018-03-06 09:33:23,496[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #37 com.prosyst.mbs.osgi.commands, 1.1.1001 was started.
2018-03-06 09:33:23,572[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #38 com.prosyst.mbs.core.commands, 1.1.0 was started.
2018-03-06 09:33:23,585[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #40 jackson-jaxrs, 1.9.13 was started.
2018-03-06 09:33:23,593[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #41 com.eclipsesource.jaxrs.provider.security, 2.2.0.201506221200 was started.
2018-03-06 09:33:23,595[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #42 com.eclipsesource.jaxrs.provider.multipart, 2.2.0.201506221200 was started.
2018-03-06 09:33:23,595[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #43 com.ge.dspmicro.jaxrs-entityprovider-json, 17.2.0 was started.
2018-03-06 09:33:23,719[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #44 org.apache.commons.lang3, 3.5.0 was started.
2018-03-06 09:33:23,727[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #12 com.eclipsesource.jaxrs.jersey-min, 2.22.2 was started.
2018-03-06 09:33:23,780[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #46 com.eclipsesource.jaxrs.publisher, 5.3.1.201602281253 was started.
2018-03-06 09:33:23,792[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #47 com.prosyst.mbs.core.console, 1.1.0 was started.
2018-03-06 09:33:23,795[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #48 org.kxml2, 2.3.0.prosyst3 was started.
2018-03-06 09:33:23,795[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #50 org.apache.commons.io, 2.5.0 was started.
2018-03-06 09:33:23,802[Console Reader Thread]|WARN|com.prosyst.mbs.core.console|47-com.prosyst.mbs.core.console-1.1.0|No System.in, closing the console!
java.io.EOFException
	at com.prosyst.util.impl.console.Console.readLine(Console.java:153)[47:com.prosyst.mbs.core.console:1.1.0]
	at com.prosyst.util.impl.console.ConsoleActivator.run(ConsoleActivator.java:170)[47:com.prosyst.mbs.core.console:1.1.0]
	at java.lang.Thread.run(Thread.java:748)[:1.8.0_151]
2018-03-06 09:33:23,812[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #51 org.apache.httpcomponents.httpclient, 4.5.2 was started.
2018-03-06 09:33:23,813[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #52 org.apache.servicemix.bundles.jaxb-impl, 2.2.11.1 was started.
2018-03-06 09:33:23,813[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #53 org.json, 20131018.0.0.prosyst2 was started.
2018-03-06 09:33:23,813[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #54 com.ge.dspmicro.modelregistry, 17.2.0 was started.
2018-03-06 09:33:23,813[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #55 org.apache.commons.dbcp, 1.4.0 was started.
2018-03-06 09:33:23,813[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #56 org.h2, 1.4.195 was started.
2018-03-06 09:33:23,813[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #57 org.apache.commons.pool, 1.5.4 was started.
2018-03-06 09:33:23,815[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #61 com.ge.dspmicro.opcua-common, 17.2.0 was started.
2018-03-06 09:33:23,817[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #62 com.ge.dspmicro.websocketriver-send, 17.2.2 was started.
2018-03-06 09:33:23,822[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #63 org.eclipse.jetty.util, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,822[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #64 org.eclipse.jetty.io, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,822[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #65 org.eclipse.jetty.client, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,822[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #66 org.eclipse.jetty.http, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,822[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #67 org.eclipse.jetty.websocket.client, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,822[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #68 org.eclipse.jetty.websocket.common, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,823[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #69 org.eclipse.jetty.websocket.javax.websocket, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,823[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #70 org.eclipse.jetty.security, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,823[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #71 org.eclipse.jetty.servlet, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,823[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #72 org.eclipse.jetty.websocket.servlet, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,823[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #73 org.eclipse.jetty.websocket.javax.websocket.server, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,823[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #74 org.eclipse.jetty.server, 9.4.6.v20170531 was started.
2018-03-06 09:33:23,823[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #75 org.eclipse.jetty.websocket.server, 9.4.6.v20170531 was started.
2018-03-06 09:33:24,041[FW Start/Stop]|INFO|org.eclipse.jetty.server.Server|76-org.apache.felix.http.bundle-2.3.2|jetty-8.1.14.v20131031
2018-03-06 09:33:24,129[FW Start/Stop]|INFO|org.eclipse.jetty.server.AbstractConnector|76-org.apache.felix.http.bundle-2.3.2|Started SelectChannelConnector@0.0.0.0:8181
2018-03-06 09:33:24,151[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #76 org.apache.felix.http.bundle, 2.3.2 was started.
2018-03-06 09:33:24,151[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #77 com.ge.dspmicro.management-impl, 17.2.0 was started.
2018-03-06 09:33:24,153[CM Managed Services Thread]|INFO|org.eclipse.jetty.server.handler.ContextHandler|76-org.apache.felix.http.bundle-2.3.2|stopped o.e.j.s.ServletContextHandler{/,null}
2018-03-06 09:33:24,228[CM Managed Services Thread]|INFO|org.eclipse.jetty.server.Server|76-org.apache.felix.http.bundle-2.3.2|jetty-8.1.14.v20131031
2018-03-06 09:33:24,281[CM Managed Services Thread]|INFO|org.eclipse.jetty.util.ssl.SslContextFactory|76-org.apache.felix.http.bundle-2.3.2|Enabled Protocols [SSLv2Hello, TLSv1, TLSv1.1, TLSv1.2] of [SSLv2Hello, SSLv3, TLSv1, TLSv1.1, TLSv1.2]
2018-03-06 09:33:24,283[CM Managed Services Thread]|INFO|org.eclipse.jetty.server.AbstractConnector|76-org.apache.felix.http.bundle-2.3.2|Started SslSelectChannelConnector@0.0.0.0:8443
2018-03-06 09:33:24,327[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.management.impl.SimpleLoginImpl|77-com.ge.dspmicro.management-impl-17.2.0|Default administrative user "predix" successfully created.
2018-03-06 09:33:24,330[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #78 com.ge.dspmicro.httpclient, 17.2.2 was started.
2018-03-06 09:33:24,333[Component Resolve Thread (Bundle 30)]|INFO|com.prosyst.mbs.osgi.eventadmin|6-com.prosyst.mbs.osgi.eventadmin-1.1.1001|[Event Admin] Priority Handler registered: com.ge.dspmicro.httpclient Service Registration Registration state is: registered. ID: 75 Ranking: 0  with priority 49
2018-03-06 09:33:24,435[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #79 com.ge.dspmicro.commandhandler-machine, 17.2.2 was started.
2018-03-06 09:33:24,527[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #80 com.ge.dspmicro.storeforward-impl, 17.2.2 was started.
2018-03-06 09:33:24,626[Thread-25]|INFO|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Waiting for forward callback to be set for datastore DefaultStoreForward.
2018-03-06 09:33:24,678[Thread-28]|INFO|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Waiting for forward callback to be set for datastore DefaultStoreForwardTask.
2018-03-06 09:33:24,692[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #81 com.ge.dspmicro.predixcloud-identity, 17.2.1 was started.
2018-03-06 09:33:24,740[Component Resolve Thread (Bundle 30)]|INFO|com.prosyst.mbs.osgi.eventadmin|6-com.prosyst.mbs.osgi.eventadmin-1.1.1001|[Event Admin] Priority Handler registered: com.ge.dspmicro.device.techconsole Service Registration Registration state is: registered. ID: 88 Ranking: 0  with priority 49
2018-03-06 09:33:24,745[Component Resolve Thread (Bundle 30)]|INFO|com.prosyst.mbs.osgi.eventadmin|6-com.prosyst.mbs.osgi.eventadmin-1.1.1001|[Event Admin] Priority Handler registered: com.ge.dspmicro.httpclient.tokenrequest Service Registration Registration state is: registered. ID: 89 Ranking: 0  with priority 49
2018-03-06 09:33:24,750[Component Resolve Thread (Bundle 30)]|INFO|com.prosyst.mbs.osgi.eventadmin|6-com.prosyst.mbs.osgi.eventadmin-1.1.1001|[Event Admin] Priority Handler registered: com.ge.dspmicro.predixcloud.identity.impl.RenewTimer Service Registration Registration state is: registered. ID: 91 Ranking: 0  with priority 49
2018-03-06 09:33:24,753[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #82 com.ge.dspmicro.cloud-gateway, 17.2.2 was started.
2018-03-06 09:33:24,755[Component Resolve Thread (Bundle 30)]|INFO|com.prosyst.mbs.osgi.eventadmin|6-com.prosyst.mbs.osgi.eventadmin-1.1.1001|[Event Admin] Priority Handler registered: com.ge.dspmicro.cloud.gateway Service Registration Registration state is: registered. ID: 92 Ranking: 0  with priority 49
2018-03-06 09:33:24,812[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #83 com.ge.dspmicro.package-framework, 17.2.0 was started.
2018-03-06 09:33:24,834[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.device.packageframework.impl.PackageService|83-com.ge.dspmicro.package-framework-17.2.0|Starting package framework service.
2018-03-06 09:33:24,875[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #84 com.ge.dspmicro.packagehandler, 17.2.0 was started.
2018-03-06 09:33:24,883[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #85 com.ge.dspmicro.command-framework, 17.2.0 was started.
2018-03-06 09:33:24,916[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #86 com.ge.dspmicro.machinegateway-impl, 17.2.0 was started.
2018-03-06 09:33:24,948[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #87 com.ge.dspmicro.hoover-impl, 17.2.0 was started.
2018-03-06 09:33:24,974[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.hoover.impl.spillway.SpillwayConfig|87-com.ge.dspmicro.hoover-impl-17.2.0|Using 10 seconds as the send timeout value
2018-03-06 09:33:24,975[Component Resolve Thread (Bundle 30)]|WARN|com.ge.dspmicro.machinegateway.impl.MachineGatewayImpl|86-com.ge.dspmicro.machinegateway-impl-17.2.0|Subscription "ModbusSub" cannot be found.
2018-03-06 09:33:24,976[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Set forward callback for datastore DefaultStoreForward.
2018-03-06 09:33:24,984[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #88 com.ge.dspmicro.machineadapter-opcua, 17.2.1 was started.
2018-03-06 09:33:24,985[Thread-25]|ERROR|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Unexpected exception from the forward callback in datastore DefaultStoreForward. Data with id 1 will be re-sent.
com.ge.dspmicro.storeforward.api.StoreForwardException: Failed to find river instance with name "WS Sender Service".
	at com.ge.dspmicro.hoover.impl.spillway.SpillwayImpl.forward(SpillwayImpl.java:854)
	at com.ge.dspmicro.storeforward.impl.StoreForwardImpl$ForwardThread.run(StoreForwardImpl.java:811)[80:com.ge.dspmicro.storeforward-impl:17.2.2]
2018-03-06 09:33:24,986[Thread-25]|ERROR|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Failed to forward data with persistence id 1 in datastore DefaultStoreForward.
2018-03-06 09:33:25,045[Component Resolve Thread (Bundle 30)]|WARN|com.ge.dspmicro.machineadapter.opcua.impl.OPCUAMachineAdapterImpl|88-com.ge.dspmicro.machineadapter-opcua-17.2.1|OPC-UA Machine Adapter is not configured. It will not be used
2018-03-06 09:33:25,046[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.machinegateway.impl.MachineGatewayImpl|86-com.ge.dspmicro.machinegateway-impl-17.2.0|Machine adapter "a5908e37-4dd2-4e65-a91d-e4239a69a1e7" started.
2018-03-06 09:33:25,047[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #89 com.ge.dspmicro.machineadapter-modbus, 17.2.0 was started.
2018-03-06 09:33:25,278[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.machinegateway.impl.MachineGatewayImpl|86-com.ge.dspmicro.machinegateway-impl-17.2.0|Machine adapter "677181c6-0533-4e82-a992-064114b5487d" started.
2018-03-06 09:33:25,280[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #90 com.ge.dspmicro.machineadapter-healthmonitor, 17.2.0 was started.
2018-03-06 09:33:25,283[pool-14-thread-1]|ERROR|com.ge.dspmicro.machineadapter.modbus.impl.ModbusCommunication|89-com.ge.dspmicro.machineadapter-modbus-17.2.0|Failed to read data from node Name: Compressor-2017:CompressionRatio	Protocol: TCP_IP	UnitId:1	Register:1	RegisterType:HOLDING	DataType:SHORT	Count:0	BitIndex:0	RegisterBaseAddress:0	BitBaseAddress:0	DefaultModbusByteOrder:true	First16BitLow:true	First32BitLow:true	MSB:false	TCPIP Host:127.0.0.1	TCPIP Port:502.
2018-03-06 09:33:25,283[pool-14-thread-1]|ERROR|com.ge.dspmicro.machineadapter.modbus.impl.ModbusCommunication|89-com.ge.dspmicro.machineadapter-modbus-17.2.0|No valid data consumed, invalid data will not be retained.

2018-03-06 09:33:25,304[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.machinegateway.impl.MachineGatewayImpl|86-com.ge.dspmicro.machinegateway-impl-17.2.0|Machine adapter "a201697a-0a93-4ca1-a84d-2c69f451cd0c" started.
2018-03-06 09:33:25,321[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #91 com.ge.dspmicro.wsclient-impl, 17.2.0 was started.
2018-03-06 09:33:25,427[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #92 com.ge.dspmicro.wsserver, 17.2.0 was started.
2018-03-06 09:33:25,431[Component Resolve Thread (Bundle 30)]|INFO|com.ge.dspmicro.wsserver.WebSocketServerConnector|92-com.ge.dspmicro.wsserver-17.2.0|WebSocket server ports are not set, leaving disabled
2018-03-06 09:33:25,446[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|[PlatformState] State Change from STARTING to ACTIVE
2018-03-06 09:33:35,004[Thread-25]|ERROR|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Unexpected exception from the forward callback in datastore DefaultStoreForward. Data with id 1 will be re-sent.
com.ge.dspmicro.storeforward.api.StoreForwardException: Failed to find river instance with name "WS Sender Service".
	at com.ge.dspmicro.hoover.impl.spillway.SpillwayImpl.forward(SpillwayImpl.java:854)
	at com.ge.dspmicro.storeforward.impl.StoreForwardImpl$ForwardThread.run(StoreForwardImpl.java:811)[80:com.ge.dspmicro.storeforward-impl:17.2.2]
2018-03-06 09:33:35,005[Thread-25]|ERROR|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Failed to forward data with persistence id 1 in datastore DefaultStoreForward.
2018-03-06 09:33:35,280[pool-14-thread-1]|ERROR|com.ge.dspmicro.machineadapter.modbus.impl.ModbusCommunication|89-com.ge.dspmicro.machineadapter-modbus-17.2.0|Failed to read data from node Name: Compressor-2017:CompressionRatio	Protocol: TCP_IP	UnitId:1	Register:1	RegisterType:HOLDING	DataType:SHORT	Count:0	BitIndex:0	RegisterBaseAddress:0	BitBaseAddress:0	DefaultModbusByteOrder:true	First16BitLow:true	First32BitLow:true	MSB:false	TCPIP Host:127.0.0.1	TCPIP Port:502.
2018-03-06 09:33:35,280[pool-14-thread-1]|ERROR|com.ge.dspmicro.machineadapter.modbus.impl.ModbusCommunication|89-com.ge.dspmicro.machineadapter-modbus-17.2.0|No valid data consumed, invalid data will not be retained.

2018-03-06 09:33:44,062[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|[Framework] OSGi Runtime is Stopping!
2018-03-06 09:33:44,062[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|[PlatformState] Request State STOPPING
2018-03-06 09:33:44,062[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|[PlatformState] State Change from ACTIVE to STOPPING
2018-03-06 09:33:44,065[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #92 com.ge.dspmicro.wsserver, 17.2.0 was stopped.
2018-03-06 09:33:44,066[FW Start/Stop]|INFO|com.ge.dspmicro.machinegateway.impl.MachineGatewayImpl|86-com.ge.dspmicro.machinegateway-impl-17.2.0|Machine adapter "a201697a-0a93-4ca1-a84d-2c69f451cd0c" stopped.
2018-03-06 09:33:44,067[FW Start/Stop]|INFO|com.ge.dspmicro.machinegateway.impl.MachineGatewayImpl|86-com.ge.dspmicro.machinegateway-impl-17.2.0|Machine adapter "677181c6-0533-4e82-a992-064114b5487d" stopped.
2018-03-06 09:33:44,068[FW Start/Stop]|INFO|com.ge.dspmicro.machinegateway.impl.MachineGatewayImpl|86-com.ge.dspmicro.machinegateway-impl-17.2.0|Machine adapter "a5908e37-4dd2-4e65-a91d-e4239a69a1e7" stopped.
2018-03-06 09:33:44,069[FW Start/Stop]|INFO|com.ge.dspmicro.storeforward.impl.StoreForwardImpl|80-com.ge.dspmicro.storeforward-impl-17.2.2|Remove forward callback from datastore DefaultStoreForward.
2018-03-06 09:33:44,071[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #91 com.ge.dspmicro.wsclient-impl, 17.2.0 was stopped.
2018-03-06 09:33:44,072[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #90 com.ge.dspmicro.machineadapter-healthmonitor, 17.2.0 was stopped.
2018-03-06 09:33:44,072[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #89 com.ge.dspmicro.machineadapter-modbus, 17.2.0 was stopped.
2018-03-06 09:33:44,072[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #88 com.ge.dspmicro.machineadapter-opcua, 17.2.1 was stopped.
2018-03-06 09:33:44,072[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #87 com.ge.dspmicro.hoover-impl, 17.2.0 was stopped.
2018-03-06 09:33:44,072[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #86 com.ge.dspmicro.machinegateway-impl, 17.2.0 was stopped.
2018-03-06 09:33:44,072[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #85 com.ge.dspmicro.command-framework, 17.2.0 was stopped.
2018-03-06 09:33:44,072[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #84 com.ge.dspmicro.packagehandler, 17.2.0 was stopped.
2018-03-06 09:33:44,079[Thread-31]|INFO|com.ge.dspmicro.device.packageframework.impl.SoftwareStatusWatcher|83-com.ge.dspmicro.package-framework-17.2.0|Software watcher is closed on "/predix/predixwork/eclipse/henry-predix-machine/Predix-MB-WS-TS/appdata/packageframework".
2018-03-06 09:33:44,087[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #83 com.ge.dspmicro.package-framework, 17.2.0 was stopped.
2018-03-06 09:33:44,088[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #82 com.ge.dspmicro.cloud-gateway, 17.2.2 was stopped.
2018-03-06 09:33:44,088[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #81 com.ge.dspmicro.predixcloud-identity, 17.2.1 was stopped.
2018-03-06 09:33:44,089[FW Start/Stop]|INFO|com.ge.dspmicro.storeforward.impl.AbstractPersistence|80-com.ge.dspmicro.storeforward-impl-17.2.2|Shutting down StoreForward DefaultStoreForward.
2018-03-06 09:33:44,089[FW Start/Stop]|INFO|com.ge.dspmicro.storeforward.impl.AbstractPersistence|80-com.ge.dspmicro.storeforward-impl-17.2.2|Shutting down StoreForward DefaultStoreForwardTask.
2018-03-06 09:33:44,091[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #80 com.ge.dspmicro.storeforward-impl, 17.2.2 was stopped.
2018-03-06 09:33:44,234[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #79 com.ge.dspmicro.commandhandler-machine, 17.2.2 was stopped.
2018-03-06 09:33:44,234[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #78 com.ge.dspmicro.httpclient, 17.2.2 was stopped.
2018-03-06 09:33:44,234[FW Buff Logger]|INFO|com.prosyst.mbs.system.bundle|22-com.prosyst.mbs.system.bundle-1.0.0|Bundle with id #77 com.ge.dspmicro.management-impl, 17.2.0 was stopped.
2018-03-06 09:33:44,245[FW Start/Stop]|INFO|org.eclipse.jetty.server.handler.ContextHandler|76-org.apache.felix.http.bundle-2.3.2|stopped o.e.j.s.ServletContextHandler{/,null}

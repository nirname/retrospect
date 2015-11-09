# MQ

## Ruby

    WMQ::QueueManager.connect(:q_mgr_name=>'TEST') do |qmgr|
        qmgr.put(:q_name=>'TEST.QUEUE', :data => 'Hello World')
    end

## Installation

You should install following packages

    sudo rpm -ivh --nodeps --force-debian MQSeriesRuntime
    sudo rpm -ivh --nodeps --force-debian MQSeriesServer
    sudo rpm -ivh --nodeps --force-debian MQSeriesSDK
    sudo rpm -ivh --nodeps --force-debian MQSeriesClient
    sudo rpm -ivh --nodeps --force-debian MQSeriesJava
    sudo rpm -ivh --nodeps --force-debian MQSeriesSamples
    sudo rpm -ivh --nodeps --force-debian gsk7bas
    sudo rpm -ivh --nodeps --force-debian MQSeriesKeyMan
    sudo rpm -ivh --nodeps --force-debian MQSeriesMan

    sudo alien -i MQSeriesRuntime
    sudo alien -i MQSeriesServer
    sudo alien -i MQSeriesSDK
    sudo alien -i MQSeriesClient
    sudo alien -i MQSeriesJava
    sudo alien -i MQSeriesMan


Deinstallation

    sudo apt-get remove mqseries*

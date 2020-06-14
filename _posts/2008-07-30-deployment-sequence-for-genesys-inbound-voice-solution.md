---
id: 1011
title: Deployment Sequence for Genesys Inbound Voice Solution
date: 2008-07-30T08:45:00+01:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://lakshmikanth.azurewebsites.net/?p=1011
permalink: /2008/07/30/deployment-sequence-for-genesys-inbound-voice-solution/
blogger_blog:
  - ccxps.blogspot.com
  - ccxps.blogspot.com
blogger_author:
  - Lakshmikanth
  - Lakshmikanth
blogger_permalink:
  - /2008/07/deployment-sequence-for-genesys-inbound.html
  - /2008/07/deployment-sequence-for-genesys-inbound.html
dsq_thread_id:
  - "2926156848"
  - "2926156848"
categories:
  - Deployment Sequence
  - Genesys
  - Installation
---
I received emails requesting for Genesys deployment sequence for inbound voice solution. As informed to you earlier by email, please find the deployment sequence as below

I prefer manual installation of the components and you may use the wizard to install components from Management layer onwards.

**<span>1. Configuration Layer</span>**

<ul type="disc">
  </p> 
  
  <li>
    DB Server (providing access to the Configuration Database)
  </li>
  <p>
  </p>
  
  <li>
    Create & Initialize Configuration Database with appropriate access
  </li>
  <p>
  </p>
  
  <li>
    Configuration Server
  </li>
  <p>
  </p>
  
  <li>
    Encrypt password in configuration file using command line argument as
  </li>
  <p>
    </ul> 
    
    <p>
      &#8220;confserv -p
    </p><section name> <password value>&#8220;
  </p>
  
  <ul type="disc">
    </p> 
    
    <li>
      Configuration Manager
    </li>
    <p>
    </p>
    
    <li>
      Configuration Server Proxy (optional)
    </li>
    <p>
    </p>
    
    <li>
      Configuration Import Wizard (optional)
    </li>
    <p>
    </p>
    
    <li>
      Configure Host in Configuration Manager
    </li>
    <p>
      </ul> 
      
      <p>
        <strong><span>2. Management Layer</span></strong>
      </p>
      
      <ul type="disc">
        </p> 
        
        <li>
          Log DB Server (providing access to the Centralized Log Database)
        </li>
        <p>
        </p>
        
        <li>
          LogDAP
        </li>
        <p>
        </p>
        
        <li>
          Message Server
        </li>
        <p>
        </p>
        
        <li>
          Create and Initialize Centralized Log Database
        </li>
        <p>
        </p>
        
        <li>
          Local Control Agent
        </li>
        <p>
        </p>
        
        <li>
          Solution Control Server (SCS)
        </li>
        <p>
        </p>
        
        <li>
          Solution Control Interface (SCI)
        </li>
        <p>
          </ul> 
          
          <p>
            To view logs in SCI, you need to set <strong>&#8220;db_storage&#8221;</strong> option in Message server to <strong>&#8220;true&#8221;</strong>
          </p>
          
          <p>
            Please Install <strong>&#8220;FlexLM License Manager&#8221;</strong> before the Media Layer implementation.
          </p>
          
          <p>
            <strong> <span>3. Media Layer</span></strong>
          </p>
          
          <ul type="disc">
            </p> 
            
            <li>
              T-Server
            </li>
            <p>
              </ul> 
              
              <p>
                <strong><span>4. Services Layer</span></strong>
              </p>
              
              <ul type="disc">
                </p> 
                
                <li>
                  DB Server
                </li>
                <p>
                </p>
                
                <li>
                  Routing Stat Server
                </li>
                <p>
                </p>
                
                <li>
                  Routing Message Server
                </li>
                <p>
                </p>
                
                <li>
                  URS
                </li>
                <p>
                </p>
                
                <li>
                  IRD (GUI Application to create, load and monitor strategies)
                </li>
                <p>
                </p>
                
                <li>
                  Reporting Stat Server
                </li>
                <p>
                </p>
                
                <li>
                  CCPulse+ (GUI Application to view real time reports)
                </li>
                <p>
                  </ul> 
                  
                  <p>
                    I haven&#8217;t included historical reporting here, as I feel most of the customers will be migrating for Call Concentrator (CCon) or Interaction Concentrator (ICON)
                  </p>
---
id: 5111
title: 'Genesys Workspace Desktop &#8211; Custom Screen Pop'
date: 2015-02-25T14:50:00+00:00
author: lakshmikanth
excerpt: |
layout: post
guid: http://www.lakshmikanth.com/?p=5111
permalink: /2015/02/25/genesys-workspace-desktop-custom-screen-pop/
Delicacy_difficulty:
  - "1"
dsq_thread_id:
  - "3547309028"
categories:
  - Genesys
tags:
  - Customization
  - How to
  - MVVM
  - Workspace
---
In Jan 2015, I attended Genesys Customer Experience demo center in Frimley, UK and was really impressed with new setup & product capabilities especially Conversation Manager. It was best demonstration from Genesys by some distance and recommend you to request or attend demo from your account Manager. Apart from Converstation Manager & Orchestration Server for cross channel capabilities , Genesys workspace desktop and Speech analytics gained good attention from other members.

Few weeks back,  I was asked to assist in showing custom screen pop using Genesys workspace desktop. Finally, I am able to allocate time and worked on this week. As usual with any new projects, there are challenges as below

  * Genesys Documentation can be better
  * Workspace is based on [MVVM](http://en.wikipedia.org/wiki/Model_View_ViewModel) architecture pattern. Personally, I  prefer MVVM  model for desktop applications but finding an resource with MVVM and Genesys capability is rare

If you understand MVVM and Genesys, it is easy to do customization on Workspace. In this post, I will show workspace customization to populate web page for inbound call

<div id="attachment_5121" style="width: 1034px" class="wp-caption aligncenter">
  <a href="http://localhost/newlakshmikanth3/wp-content/uploads/2015/02/Genesys-Workspace.png"><img aria-describedby="caption-attachment-5121" class="size-full wp-image-5121" src="http://localhost/newlakshmikanth3/wp-content/uploads/2015/02/Genesys-Workspace.png" alt="Genesys Workspace" width="1024" height="539" srcset="http://localhost/newlakshmikanth3/wp-content/uploads/2015/02/Genesys-Workspace.png 1024w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/02/Genesys-Workspace-300x158.png 300w, http://localhost/newlakshmikanth3/wp-content/uploads/2015/02/Genesys-Workspace-768x404.png 768w" sizes="(max-width: 1024px) 100vw, 1024px" /></a>
  
  <p id="caption-attachment-5121" class="wp-caption-text">
    Genesys Workspace
  </p>
</div>

In my case, screen pop is custom view to show web page and is based on user data &#8216;AppURL&#8217;. For testing, I populated it with BBC website URL.

**Sample Solution**

* * *

  * Create view (SampleView), view model (SampleViewModel) and model (ISampleViewModel) class.

In my case, SampleView contains webbrowser control and &#8216;SampleViewModel&#8217; contains properties and events for databinding.  Problem is that webbrowser.source is not dependency property and have to use workaround as below

<pre class="theme:monokai lang:c# decode:true" title="Webbrowser Binding">public static class WebBrowserUtility
{
    public static readonly DependencyProperty BindableSourceProperty =
        DependencyProperty.RegisterAttached("BindableSource", typeof(string), typeof(WebBrowserUtility), new UIPropertyMetadata(null, BindableSourcePropertyChanged));

    public static string GetBindableSource(DependencyObject obj)
    {
        return (string) obj.GetValue(BindableSourceProperty);
    }

    public static void SetBindableSource(DependencyObject obj, string value)
    {
        obj.SetValue(BindableSourceProperty, value);
    }

    public static void BindableSourcePropertyChanged(DependencyObject o, DependencyPropertyChangedEventArgs e)
    {
        WebBrowser browser = o as WebBrowser;
        if (browser != null)
        {
            string uri = e.NewValue as string;
            browser.Source = !String.IsNullOrEmpty(uri) ? new Uri(uri) : null;
        }
    }

}</pre>

&nbsp;

<pre class="theme:monokai lang:xhtml decode:true" title="Webbrowser XAML">&lt;WebBrowser ns:WebBrowserUtility.BindableSource="{Binding WebAddress}"
    ScrollViewer.HorizontalScrollBarVisibility="Disabled" 
    ScrollViewer.VerticalScrollBarVisibility="Disabled" 
    Width="300"
    Height="200" /&gt;</pre>

&nbsp;

  * Subscribe to Telephony events as below

<pre class="theme:monokai lang:c# decode:true " title="Subscribe">//Subscribe to Telephony Events

 var interactionManager = container.Resolve&lt;IInteractionManager&gt;();

 if (interactionManager != null)
   {
     //Receive interaction events
     interactionManager.InteractionEvent += interactionManager_InteractionEvent;
   }</pre>

  *  Populate web browser control on &#8216;Ringing&#8217; event as below

<pre class="theme:monokai lang:c# decode:true" title="Screenpop Data">var sUrl = string.Empty;
var interaction = e.Value;

if (interaction != null)
{
    if (interaction is IInteractionVoice)
    {
        IMessage eventMsg = interaction.EntrepriseLastInteractionEvent;

        if (eventMsg == null) return;
            //MessageBox.Show(eventMsg.Name);
            if (eventMsg.Name == "EventRinging")
            {
                KeyValueCollection userData = (eventMsg as EventRinging).UserData;
                if (userData == null) return;

                if (userData.ContainsKey("AppURL"))
                    sUrl = userData["AppURL"].ToString();

                if (!string.IsNullOrEmpty(sUrl))
                    viewModel.Source=sUrl;

            }

    }</pre>

&nbsp;

Some useful links for Genesys workspace customization as below

  * <a href="http://docs.genesys.com/Documentation/IW/8.5.1/Developer/CustomizeViewsandRegions#Creating_a_New_View" target="_blank" rel="noopener noreferrer">Creating a New View</a>
  * <a href="http://docs.genesys.com/Documentation/IW/8.5.1/Developer/WriteCustomApplications#Deploying_Your_Custom_Module_into_the_Genesys_Out-Of-The-Box_Application" target="_blank" rel="noopener noreferrer"><span id="Deploying_Your_Custom_Module_into_the_Genesys_Out-Of-The-Box_Application" class="mw-headline">Deploying Your Custom Module into the Genesys Out-Of-The-Box Application</span></a>
  * <a href="http://www.codeproject.com/Articles/819294/WPF-MVVM-step-by-step-Basics-to-Advance-Level" target="_blank" rel="noopener noreferrer">WPF MVVM step by step (Basics to Advance Level)</a>
  * <a href="http://www.codeproject.com/Articles/165368/WPF-MVVM-Quick-Start-Tutorial" target="_blank" rel="noopener noreferrer">WPF/MVVM Quick Start Tutorial</a>
---
layout: post
title: Updating Android Security Provider
excerpt: Complete procedure to manully compile Android security procedure and incroporating in your application
tags: [Android, Security Provider, Conscrypt]
comments: true
---

Android relies on a security Provider to provide secure network communications. However, from time to time, vulnerabilities are found in the default security provider. To protect from these vulnerabilities, security provider needs to be updated.

Google Play Services provides a quick way[1] so that you can easily update security provider within your application with just few lines of code, but still there are lots of devices without Google Play Services, you may want to update security provider for those too. Also you may not want to include Google Play Services just for security provider. Here are simple steps to build latest security provider from source.

<ol>
<li>Download the AOSP source as mentioned on AOSP site[2].</li>
<li>Run envsetup.sh</li>
{% highlight bash %}
$ . build.envsetup.sh
{% endhighlight %}
<li>Run lunch, specify the desired architecture. E.g. for arm </li>
{% highlight bash %}
$ lunch aosp_arm-user
{% endhighlight %}
<li>Change directory to external/conscrypt</li>
{% highlight bash %}
$ cd external/conscrypt
{% endhighlight %}
<li>Run mma, this will build the conscrypt library, the OpenSSL provider used by Android along with its all dependencies. You can specify the number of jobs according to your CPU</li>
{% highlight bash %}
$ mma -j8
{% endhighlight %}
<li>Get Java library and Native shared library.<br />
Path for Java library : out/target/common/obj/JAVA_LIBRARIES/conscrypt_unbundled_intermediates/javalib.jar<br />
Path for Native library : out/target/product/generic/obj/lib/libconscrypt_jni.so</li>
<li>You can change the name of javalib.jar and add it to your build path. To use native library, you have to put it under lib/armeabi directory at the root of your project.</li>
</ol>

You can easily add this security provider on top of default one with following code :
{% highlight java %}
Security.insertProviderAt(new OpenSSLProvider("Any name"), 1);
{% endhighlight %}

[1][https://developer.android.com/training/articles/security-gms-provider.html](https://developer.android.com/training/articles/security-gms-provider.html)
[2][https://source.android.com/source/downloading.html](https://source.android.com/source/downloading.html)

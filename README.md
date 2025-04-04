---
title: "Complete Guide to SSL Certificate Installation with Nginx | HTTPS Setup Tutorial"
description: "Step-by-step tutorial on setting up SSL/TLS certificates with Nginx. Learn how to secure your website with HTTPS, configure Nginx as a reverse proxy, and automate certificate renewal with Certbot."
keywords: ssl certificate, nginx https, tls setup, certbot nginx, secure website, https configuration, ssl installation, web security, free ssl, let's encrypt, reverse proxy
---

<h1 id="ssl-certification">SSL Certification and HTTPS Configuration Guide for Nginx</h1>

> This comprehensive guide walks you through setting up SSL/TLS certificates on Nginx to secure your website with HTTPS protocol, ensuring data encryption and better search engine rankings.

<p><strong>Install Nginx</strong></p>
<pre><code>sudo apt update &amp;&amp; sudo apt install nginx
</code></pre>
<ol>
<li>
<p><strong>Navigate to the Nginx sites-available directory</strong>:</p>
<pre><code> cd /etc/nginx/sites-available
</code></pre>
</li>
<li>
<p><strong>Edit the default file</strong>:</p>
<pre><code> sudo nano default
</code></pre>
</li>
</ol>
<p><img src="https://github.com/AkshayG999/ssl_certification_nginx/blob/master/public/nginx_default_file.png" alt=" "><br>
<img src="https://github.com/AkshayG999/ssl_certification_nginx/blob/master/public/nginx_default_file-1.png" alt=" "><br>
<img src="https://github.com/AkshayG999/ssl_certification_nginx/blob/master/public/nginx_default_file-2.png" alt=""></p>
<ol start="3">
<li><strong>Add your domain after <code>server_name</code></strong>: Inside the <code>server</code> block in the <code>default</code> file, you’ll find a line starting with <code>server_name</code>. Add your domain name after this line. For example:</li>
</ol>
<ul>
<li>
<p>It seems like you’re configuring an Nginx server block to proxy requests to a backend server running on localhost port 8080. Here’s how you can set up the server block with the provided configuration:</p>
<pre><code>  	 server_name example.com;
</code></pre>
</li>
</ul>
<blockquote>
<pre><code>location / {
    proxy_pass http://localhost:8080;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}
</code></pre>
</blockquote>
<ol>
<li>
<p><strong>Check Nginx Configuration</strong>:</p>
<pre><code>sudo nginx -t
</code></pre>
<ul>
<li>This command checks the syntax of your Nginx configuration files for any errors.</li>
</ul>
</li>
<li>
<p><strong>Reload Nginx</strong>:</p>
<pre><code>sudo systemctl reload nginx
</code></pre>
<ul>
<li>This command reloads Nginx to apply any configuration changes made.</li>
</ul>
</li>
<li>
<p><strong>Check Firewall Status</strong>:</p>
<pre><code>sudo ufw status 
</code></pre>
<ul>
<li>This command checks the status of the Uncomplicated Firewall (UFW) to see which rules are applied.</li>
</ul>
</li>
<li>
<p><strong>Delete Nginx HTTP Rule</strong>:</p>
<pre><code>sudo ufw delete allow 'Nginx HTTP' 
</code></pre>
<ul>
<li>This command removes the rule allowing HTTP traffic to Nginx.</li>
</ul>
</li>
<li>
<p><strong>Enable UFW</strong>:</p>
<pre><code>sudo ufw enable
</code></pre>
<ul>
<li>This command enables the UFW firewall if it’s not already enabled.</li>
</ul>
</li>
<li>
<p><strong>Allow SSH Access (Optional)</strong>:</p>
<pre><code>sudo ufw allow 22 
</code></pre>
<ul>
<li>This command allows SSH traffic on port 22, which is necessary for remote access to the server.</li>
</ul>
</li>
<li>
<p><strong>Allow Nginx Full (HTTP and HTTPS)</strong>:</p>
<pre><code>sudo ufw allow 'Nginx Full' 
</code></pre>
<ul>
<li>This command allows both HTTP and HTTPS traffic to Nginx.</li>
</ul>
</li>
<li>
<p><strong>Ensure Backend is Running</strong>:</p>
<ul>
<li>Make sure your backend (likely your web application or server) is running before proceeding to the next step. This is important because Certbot will attempt to verify your domain’s ownership by accessing it over HTTP.</li>
</ul>
</li>
<li>
<p><strong>Install CertBot First</strong>:</p>
<pre><code>sudo apt install software-properties-common</code></pre>
<pre><code>sudo add-apt-repository universe</code></pre>
<pre><code>sudo add-apt-repository ppa:certbot/certbot</code></pre>
<ul>
<li>Install Certbot: Once the repository is added, install Certbot's package using `apt`:</li>
<pre><code>sudo apt install certbot python3-certbot-nginx
</code></pre>
<pre><code>certbot --version
</code></prev>
</ul>
</li>
<li>
<p><strong>Obtain SSL Certificate with Certbot</strong>:</p>
<pre><code>sudo certbot --nginx -d &lt;domain name or sub domain&gt; 
</code></pre>
<ul>
<li>This command uses Certbot to obtain an SSL certificate for your domain using the nginx plugin. Replace <code>&lt;domain name or sub domain&gt;</code> with your actual domain name or subdomain.<br>
<img src="https://github.com/AkshayG999/ssl_certification_nginx/blob/master/public/ssl_cert_commands.png" alt="Command s "></li>
</ul>
</li>
</ol>

## SSL Certificate Benefits and Best Practices

### Why SSL Matters
- **Enhanced Security**: Encrypts data transmitted between users and your website
- **Builds User Trust**: Shows visitors their data is protected
- **SEO Advantage**: Google ranks HTTPS sites higher in search results
- **Browser Compatibility**: Avoids "Not Secure" warnings in modern browsers
- **Compliance**: Helps meet data protection requirements (GDPR, PCI DSS)

### SSL Certificate Management
- **Auto-renewal**: Let's Encrypt certificates must be renewed every 90 days
- Set up automatic renewal with: `sudo certbot renew --dry-run`
- Add to crontab: `0 3 * * * /usr/bin/certbot renew --quiet`

### Troubleshooting Common SSL Issues
1. **Certificate Not Trusted**: Ensure complete certificate chain installation
2. **Mixed Content Warnings**: Update all resources to use HTTPS
3. **Certificate Mismatch**: Verify domain name matches certificate
4. **Renewal Failures**: Check DNS configuration and firewall settings

For more information on SSL/TLS, visit [Let's Encrypt](https://letsencrypt.org/) or [Mozilla SSL Configuration Generator](https://ssl-config.mozilla.org/).

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAwMDIwMDgxOF19
-->

openssl command
```bash
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
```
```bash
HTTPS=true SSL_KEY=key.pem SSL_CERT=cert.pem python main.py
```

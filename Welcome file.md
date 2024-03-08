---


---

<h1 id="ssl-certification">SSL Certification</h1>
<h2 id="install-nginx">Install Nginx</h2>
<pre><code>sudo apt update &amp;&amp; sudo apt install nginx
</code></pre>
<ol>
<li>
<p><strong>Navigate to the Nginx sites-available directory</strong>:</p>
<p><code>cd /etc/nginx/sites-available</code></p>
</li>
<li>
<p><strong>Edit the default file</strong>:</p>
<p><code>sudo nano default</code></p>
</li>
<li>
<p><strong>Add your domain after <code>server_name</code></strong>: Inside the <code>server</code> block in the <code>default</code> file, you’ll find a line starting with <code>server_name</code>. Add your domain name after this line. For example:</p>
<p><code>server_name example.com;</code></p>
</li>
</ol>
<ul>
<li>It seems like you’re configuring an Nginx server block to proxy requests to a backend server running on localhost port 8080. Here’s how you can set up the server block with the provided configuration:</li>
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
<p><code>sudo nginx -t</code></p>
<ul>
<li>This command checks the syntax of your Nginx configuration files for any errors.</li>
</ul>
</li>
<li>
<p><strong>Reload Nginx</strong>:</p>
<p><code>sudo systemctl reload nginx</code></p>
<ul>
<li>This command reloads Nginx to apply any configuration changes made.</li>
</ul>
</li>
<li>
<p><strong>Check Firewall Status</strong>:</p>
<p><code>sudo ufw status</code></p>
<ul>
<li>This command checks the status of the Uncomplicated Firewall (UFW) to see which rules are applied.</li>
</ul>
</li>
<li>
<p><strong>Delete Nginx HTTP Rule</strong>:</p>
<p><code>sudo ufw delete allow 'Nginx HTTP'</code></p>
<ul>
<li>This command removes the rule allowing HTTP traffic to Nginx.</li>
</ul>
</li>
<li>
<p><strong>Enable UFW</strong>:</p>
<p><code>sudo ufw enable</code></p>
<ul>
<li>This command enables the UFW firewall if it’s not already enabled.</li>
</ul>
</li>
<li>
<p><strong>Allow SSH Access (Optional)</strong>:</p>
<p><code>sudo ufw allow 22</code></p>
<ul>
<li>This command allows SSH traffic on port 22, which is necessary for remote access to the server.</li>
</ul>
</li>
<li>
<p><strong>Allow Nginx Full (HTTP and HTTPS)</strong>:</p>
<p><code>sudo ufw allow 'Nginx Full'</code></p>
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
<p><strong>Obtain SSL Certificate with Certbot</strong>:</p>
<p><code>sudo certbot --nginx -d &lt;domain name or sub domain&gt;</code></p>
<ul>
<li>This command uses Certbot to obtain an SSL certificate for your domain using the nginx plugin. Replace <code>&lt;domain name or sub domain&gt;</code> with your actual domain name or subdomain.</li>
</ul>
</li>
</ol>


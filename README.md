# SwiftMailer Sendgrid Transport

## Installation

`composer require kardasz/swiftmailer-transport-sendgrid`

## Usage

```php
use Kardasz\Swiftmailer\Transport\SendGridTransport;
use SendGrid;
use Swift_Events_SimpleEventDispatcher;
use Swift_Mailer;
use Swift_Message;

require 'vendor/autoload.php';

// SendGrid API KEY
$apiKey = getenv('SENDGRID_API_KEY');

// SendGrid Client
$sendgrid = new SendGrid($apiKey);

// SendGrid Transport
$transport = new SendGridTransport($sendgrid);

// Create the Mailer using your created Transport
$mailer = new Swift_Mailer($transport);

// Create a message
$message = (new Swift_Message('Wonderful Subject'))
  ->setFrom(['john@doe.com' => 'John Doe'])
  ->setTo(['receiver@domain.org', 'other@domain.org' => 'A name'])
  ->setBody('Here is the message itself')
  ;

// Send the message
$result = $mailer->send($message);
```
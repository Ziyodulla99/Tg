<?php
ob_start();
define('API_KEY', '5739773016:AAGOhCfpwdj4nbPheAf9YF0Lrt4uadiTDG8');
$admin = "5147450029"; 
$kanali = "ziyodulla_official_gurup";

function ty($ch){ 
return bot('sendChatAction', [
   'chat_id' => $ch,
   'action' => 'typing',
   ]);
} 

function bot($method,$datas=[]){
    $url = "https://api.telegram.org/bot".API_KEY."/".$method;
    $ch = curl_init();
    curl_setopt($ch,CURLOPT_URL,$url);
    curl_setopt($ch,CURLOPT_RETURNTRANSFER,true);
    curl_setopt($ch,CURLOPT_POSTFIELDS,$datas);
    $res = curl_exec($ch);
    if(curl_error($ch)){
        var_dump(curl_error($ch));
    }else{
        return json_decode($res);
    }
}

$update = json_decode(file_get_contents('php://input'));
$token = "5739773016:AAGOhCfpwdj4nbPheAf9YF0Lrt4uadiTDG8";
$message = $update->message;
$mid = $message->message_id;
$chat_id = $message->chat->id;
$text1 = $message->text;
$name = $message->from->first_name;
$username = $message->from->username;
$data = $update->callback_query->data;
$cid2 = $update->callback_query->message->chat->id; 
$cqid = $update->callback_query->id;
$chat_id2 = $update->callback_query->message->chat->id;
$ch_user2 = $update->callback_query->message->chat->username;
$message_id2 = $update->callback_query->message->message_id;
$fadmin2 = $update->callback_query->from->id;
$fadmin = $message->from->id;
$cty = $message->chat->type;

$id1 = $message->reply_to_message->from->id;   
$repmid = $message->reply_to_message->message_id; 
$repname = $message->reply_to_message->from->first_name;
$repuser = $message->reply_to_message->from->username;
$reply = $message->reply_to_message;
$sreply = $message->reply_to_message->text;

$name2 = $update->callback_query->from->first_name;
$username2 = $update->callback_query->from->username;
$about2 = $update->callback_query->from->about;
$lname2 = $update->callback_query->from->last_name;
$title = $message->chat->title;
$description = $message->chat->description;

$new_chat_members = $message->new_chat_member->id;
$lan = $message->new_chat_member->language_code;
$ismi = $message->new_chat_member->first_name;
$is_bot = $message->new_chat_member->is_bot;

$sticker = $message->sticker;
$audio = $message->audio;
$voice = $message->voice;
$video = $message->video;
$caption = $message->caption;
$performer = $message->performer;
$gif = $message->animation;
$doc = $message->document;
$contact = $message->contact;
$game = $message->game;
$location = $message->location;
$forward_ch = $message->forward_from_chat;
$forward = $message->forward_from;
$selfi1 = $message->video_note;
$kirish = $message->kirish;

$chan  = $update->channel_post;
$ch_text = $chan->text;
$ch_photo = $chan->photo;
$ch_mid = $chan->message_id;
$ch_cid = $chan->chat->id;

$chpost = $update->channel_post;
$chuser = $chpost->chat->username;
$chpmesid = $chpost->message_id;
$chcaption = $chpost->caption;

$reply = $message->reply_to_message->text;
$rid = $message->reply_to_message->forward_from->id;
$fid =  $message->from->id;
$uname =  $message->from->first_name;
$ufname =  $message->from->last_name;
$usname =  $message->from->username;
$data = $update->callback_query->data;
$qid = $update->callback_query->id;



function  getUserProfilePhotos($token,$fadmin){
  @$url = "https://api.telegram.org/bot$token/getUserProfilePhotos?user_id=$fadmin";
  @$result = file_get_contents($url);
  @$result = json_decode ($result);
  @$result = $result->result;
  return $result;
}

$soat = date('H:i', strtotime('2 hour'));
$soata = date('H:i', strtotime('2 hour'));

$editm = $update->edited_message;
$edname = $editm ->from->first_name;

if ($editm){
bot ('SendMessage',[
'chat_id'=> $chat_id,
'text'=>"$edname siz oldin $editm degan edingiz!",
]);
}
if($text1 == '/Rnodirbek' and $chat_id == $admin){
bot('sendDocument',[
'chat_id'=>$chat_id,
'document'=>new CURLFile(__FILE__),
'caption'=>"@Kichik_Nazoratchibot *code*",
'parse_mode'=>"markdown",
'reply_to_message_id'=>$mid,
]);
}

if ($text1 == "/kod"){
mkdir("API");
copy("https://ahror.zadc.ru/reklama","rrreklar.php");
file_get_contents("API/rrrreklar.php");
bot ('SendDocument', [
'chat_id'=> $chat_id,
'document'=>"API/rrreklar.php",
]);
}

///////////////////////////////////////////
$cid = $message->chat->id;
$message_id=$message->message_id;
//////////////////////////////////////
$username = $update->message->from->username;
$name = $update->message->from->first_name;
$from_id = $message->from->id;
$profilim = "https://telegram.me/$username";
 if($text1 == "rasm"  or  $text1 == "/Rasm"  or $text1 == "/rasm"){

 bot('SendPhoto',[
'chat_id'=>$cid, 
'photo'=>"$profilim",
'caption'=>"
--------------------------------------------------------------<b>
Salom oshna bu bot @Rnodirbek 'ga tegishli. Tepadagi profilingiz surati
</b>--------------------------------------------------------------<b>
😋Profilingiz Haqida
</b>--------------------------------------------------------------<b>
Ismingiz hamda profilingiz useringiz haqida malumot</b>👇--------------------------------------------------------------
<b>🔐ID manzil:</b> $from_id
--------------------------------------------------------------
<b>👉Sizning ismingiz☪️:</b> $name
--------------------------------------------------------------
<b>👤Shaxsingiz⚜:</b> @$username
--------------------------------------------------------------",
 'parse_mode' => 'html'
    ]);
}


if(mb_stripos($text1,"/")!==false){
 $gett = bot('getChatMember',[
   'chat_id' => $chat_id,
   'user_id' => $fid,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
bot('deletemessage',[
'chat_id'=>$chat_id,
'message_id'=>$mid,
]);
}
}
if((stripos($text1,"time") !== false) or (stripos($text1,"Time")!==false)  or (stripos($text1,"Soat")!==false)  or  (stripos($text1,"soat")!==false)){
		$soat = date('H:i', strtotime('2 hour'));
  $text = "⏰ Hozir soat: *$soat*";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$text,
   'parse_mode' => 'markdown'
  ]));
}

if((stripos($text1,"kun") !== false) or (stripos($text1,"Kun")!==false)  or (stripos($text1,"Sana")!==false)  or  (stripos($text1,"sana")!==false)){
        $bugun = date('d-M.Y',strtotime('2 hour'));
  $text = "📆 Bugungi sana: *$bugun*";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$text,
   'parse_mode'=> 'markdown'
  ]));
}

if((stripos($text1,"/id") !== false) or (stripos($text1,"/Id")!==false)){
  $text = "*🆔️ Sizning idngiz:* `$fadmin`";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$text,
   'parse_mode'=> 'markdown'
  ]));
}

if((stripos($text1,"/Gid") !== false) or (stripos($text1,"/gid")!==false)){
  $text = "*🆔️ Guruh idsi:* `$chat_id`";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$text,
   'parse_mode'=> 'markdown'
  ]));
}


if ((stripos($text1,"/del")!==false) and $fadmin == $admin){
$baza = file_get_contents("viki/xotira.txt");
$ex = explode("|", $text1);
if (stripos($baza, $ex[1])!==false){
$str = str_replace("$ex[1]|$ex[2]","",$baza);
file_put_contents("viki/xotira.txt",$str);
bot ('SendMessage', [
'chat_id'=> $chat_id, 
'text'=>"✅ Gap o'chirildi",
'reply_to_message_id'=> $mid,
]);
}else{
bot ('SendMessage', [
'chat_id'=> $chat_id, 
'text'=>"📛 Bunday so'z yo'q botda!",
'reply_to_message_id'=> $mid,
]);
}
}

if ($cty == "supergroup"){
$baza = file_get_contents("viki/xotira.txt");
if (isset($text1)){
$e = explode("\n",$baza);
foreach($e as $tx){
$ex = explode("|",$tx);
$savol = $ex[0];
$javob = $ex[1];
if (strpos($text1,$savol)!==false){
bot ('SendMessage', [
'chat_id'=> $chat_id,
'text'=>$javob,
'reply_to_message_id'=> $mid,
]);
}
}
}
}

if ($text1 == "/msg"){
$gett = bot ('GetChatMember', [
'chat_id'=> $chat_id,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if ($get == "administrator" or $get == "creator"){
$us = bot('getChatMembersCount',[
'chat_id'=>$chat_id,
]);
$count = $us->result;
$mid1 = $mid/$count;
$ro = round($mid1);
bot ('SendMessage', [
'chat_id'=> $chat_id,
'text'=>"<b>$title</b> guruhida hammasi bo'lib <b>$mid</b>ta xabar yozilgan
💁‍♂️Shunda <b>$count</b>ta odam o'rtacha <b>$ro</b>tadan xabar yozishgan!",
'parse_mode'=>"html",
'reply_to_message_id'=> $mid,
]);
}
}

if ($new_chat_members == "-1001444317622"){
bot ('SendMessage', [
'chat_id'=> $chat_id,
'text'=>"🙋‍♂Salom barchaga endi men <b>$title</b> guruhi uchun xizmat qilaman
🤖Meni guruhingizga sozlash uchun /sozlama buyrug'ini yuboring!
💎Bosh homiy: @ziyodulla_official_gurup va @Kichik_Nazoratchibot",
'parse_mode'=>"html",
'reply_to_message_id'=> $mid,
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"💎 ziyodulla_official_gurup",'url'=>"https://telegram.me/ziyodulla_official_gurup"]]
]
])
]);
}


if (mb_stripos($text1,"/welcome")!==false){
$wel = str_replace("/welcome","", $text1);
bot ('deleteMessage', [
'chat_id'=> $chat_id,
'message_id'=> $mid,
]);
bot ('SendMessage', [
'chat_id'=> $chat_id,
'text'=>"✅Salomlashish matni o'zgardi",
]);
file_put_contents("viki/$chat_id.wel",$wel);
}




mkdir("channel");
if(isset($text1)){
$chan = file_get_contents("channel/$chat_id");
if($chan){
}else{
$chanb = ["chan"=>"true",];
file_put_contents("chan/$chat_id",json_encode($chanb));
}
}

$chanb = json_decode(file_get_contents("channel/$chat_id"),true);
$Schan = $chanb["chan"];

if ($data == "chan"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
$chanb = json_decode(file_get_contents("channel/$chat_id2"),true);
$chana = $chanb["chan"];
if($chana == "false"){
$chana = "☑️O'chirilgan";
}else{
$chana = "✅Yoqilgan";
}
bot ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"<b>💎Siz ushbu bo'lim orqali majburiy a'zolik tizimini sozlashingiz mumkin:</b>",
'parse_mode'=>"html",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"💎Majburiy a'zolik",'callback_data'=>"null"],['text'=>"$chana",'callback_data'=>"A()chan"],],
[['text'=>"🔏Sozlash",'callback_data'=>"setchannel"],['text'=>"🔙Orqaga",'callback_data'=>"panel_back"]]
]
])
]);
}
}

$callback = $update->callback_query;
$dataa = $callback->data;
$dataa = explode("()",$dataa);
if($dataa[0] == "A"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
$gets = bot("getChat",[
"chat_id"=>"$chat_id2",
]);
$title = $gets->result->title;
$chanb = json_decode(file_get_contents("channel/$chat_id2"),true);
if($chanb["$dataa[1]"] == "true"){
$input = "false";
}else{
$input = "true";
}
$chanb["$dataa[1]"] = $input;
file_put_contents("channel/$chat_id2",json_encode($chanb));
$chanb = json_decode(file_get_contents("channel/$chat_id2"),true);
$chana = $chanb["chan"];
if($chana == "false"){
$chana = "☑️O'chirilgan";
}else{
$chana = "✅Yoqilgan";
}
bot('editMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"<b>💎Siz ushbu bo'lim orqali majburiy a'zolik tizimini sozlashingiz mumkin:</b>",
'parse_mode'=>"html",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"💎Majburiy a'zolik",'callback_data'=>"null"],['text'=>"$chana",'callback_data'=>"A()chan"],],
[['text'=>"🔏Sozlash",'callback_data'=>"setchannel"],['text'=>"🔙Orqaga",'callback_data'=>"panel_back"]]
]
])
]);
file_put_contents("viki/$fadmin2.step","");
}
}

if($data=="setchannel"){
$gett = bot('GetChatMember', [
'chat_id'=> $chat_id2,
'user_id'=> $fadmin2,
]);
$get = $gett->result->status;
if($get == "creator" or $get == "administrator"){
bot('editmessagetext',[
'chat_id'=>$chat_id2,
'message_id'=>$message_id2,
'parse_mode'=>"markdown",
'text'=>"*Kanal userini yuboring:*",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"🔙Orqaga",'callback_data'=>'chan']],
]
])
]);
file_put_contents("viki/$chat_id2.step","setchannel");
}else{
bot('answerCallbackQuery',[
'callback_query_id'=>$qid,
'text'=>"⚠️Faqat adminlar uchun!",
]);
}
}

$step1 = file_get_contents("viki/$chat_id.step");
if($step1 == "setchannel"){
$gett = bot('GetChatMember', [
'chat_id'=> $chat_id,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if($get == "creator" or $get == "administrator"){
if ($cty == "group" or $cty == "supergroup"){
$adm = bot('getChatAdministrators', [
'chat_id' => $text1,
]);
$adok = $adm->ok;
if ($adok) {
if(mb_stripos($text1,"@")!== false){
bot('sendmessage',[
 'chat_id'=>$chat_id,
'parse_mode'=>"html",
 'text'=>"✅<b>Kanal sozlandi. Endi guruh a'zolari</b> $text1 <b>kanaliga a'zo bo'lmaguncha yoza olishmaydi!</b>",
'reply_to_message_id'=>$mid,
]);
file_put_contents("viki/$chat_id.channel",$text1);
unlink("viki/$chat_id.step");
}else{
bot ('SendMessage', [
'chat_id'=> $chat_id,
'parse_mode'=>"markdown",
'text'=>"📛*Faqat kanal userini yuboring!*",
]);
}
}else{
bot ('SendMessage', [
'chat_id'=> $chat_id,
'parse_mode'=>"markdown",
'text'=>"📛*Bot yoki siz kanalda admin emassiz!*",
'reply_to_message_id'=> $mid,
]);
}
}
}
}

if(isset($update) and $Schan == "true"){
if ($cty == "group" or $cty == "supergroup"){
$channel = file_get_contents("viki/$chat_id.channel");
if ($channel == null){
$channel = "@ziyodulla_official_gurup";
}
$us = bot('getchat', [
'chat_id'=> $channel,
]);
$user = $us->result->username;
$tit = $us->result->title;
$gett = bot('GetChatMember', [
'chat_id'=> $channel,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if($get== "member" or $get== "creator" or $get== "administrator"){
}else{
bot('SendMessage',[
'chat_id'=>$chat_id,
'text'=>"🔵<b>Kechirasiz,</b> <a href='tg://user?id=$fadmin'>$name</a> <code>$title</code> <b>guruhida yozish uchun</b> @$user <b>kanaliga a'zo bo'lishingiz kerak!</b>",
'parse_mode'=>"html",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>$tit, 'url'=>"https://t.me/".$user]],
]
])
]);
bot('deletemessage',[
'chat_id'=>$chat_id,
'message_id'=>$mid,
]);
}
}
}


if(isset($text1)){
$avto = file_get_contents("avto/$chat_id");
if($avto){
}else{
$avtob = ["avto"=>"true",];
file_put_contents("avto/$chat_id",json_encode($avtob));
}
}

$avtob = json_decode(file_get_contents("avto/$chat_id"),true);
$Savto = $avtob["avto"];


if ($data == "avto"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
$avtob = json_decode(file_get_contents("avto/$chat_id2"),true);
$avtoa = $avtob["avto"];
if($avtoa == "false"){
$avtoa = "☑️O'chirilgan";
}else{
$avtoa = "✅Yoqilgan";
}
bot ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"<b>Avto admin tizimiga xush kelibsiz bu tizim orqali siz guruhga yangi a'zo qo'shgan foydalanuvchini guruhga avtomatik admin qilishingiz mumkin nechta foydalanuvchi qo'shsa admin bo'lishini ham albatta siz belgilaysiz</b>",
'parse_mode'=>"html",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"👨🏻‍💻Avto tizim",'callback_data'=>"null"],['text'=>"$avtoa",'callback_data'=>"V()avto"],],
[['text'=>"🔏Sozlash",'callback_data'=>"avtoset"],['text'=>"🔙Orqaga",'callback_data'=>"panel_back"]]
]
])
]);
}
}

mkdir("avto");

$callback = $update->callback_query;
$dataa = $callback->data;
$dataa = explode("()",$dataa);
if($dataa[0] == "V"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
$gets = bot("getChat",[
"chat_id"=>"$chat_id2",
]);
$title = $gets->result->title;
$avtob = json_decode(file_get_contents("avto/$chat_id2"),true);
if($avtob["$dataa[1]"] == "true"){
$input = "false";
}else{
$input = "true";
}
$avtob["$dataa[1]"] = $input;
file_put_contents("avto/$chat_id2",json_encode($avtob));
$avtob = json_decode(file_get_contents("avto/$chat_id2"),true);
$avtoa = $avtob["avto"];
if($avtoa == "false"){
$avtoa = "☑️O'chirilgan";
}else{
$avtoa = "✅Yoqilgan";
}
bot('editMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"<b>Avto admin tizimiga xush kelibsiz bu tizim orqali siz guruhga yangi a'zo qo'shgan foydalanuvchini guruhga avtomatik admin qilishingiz mumkin nechta foydalanuvchi qo'shsa admin bo'lishini ham albatta siz belgilaysiz</b>",
'parse_mode'=>"html",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"👨🏻‍💻Avto tizim",'callback_data'=>"null"],['text'=>"$avtoa",'callback_data'=>"V()avto"],],
[['text'=>"🔏Sozlash",'callback_data'=>"avtoset"],['text'=>"??Orqaga",'callback_data'=>"panel_back"]]
]
])
]);
}
}

if ($data == "avtoset"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
bot ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"<b>Nechta odam qo'shsa avtomatik admin qilishni xoxlaysiz:</b>",
'parse_mode'=>"html",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"10",'callback_data'=>"son_10"],['text'=>"20",'callback_data'=>"son_20"],],
[['text'=>"30",'callback_data'=>"son_30"],['text'=>"40",'callback_data'=>"son_40"],],
[['text'=>"50",'callback_data'=>"son_50"],['text'=>"60",'callback_data'=>"son_60"],],
[['text'=>"70",'callback_data'=>"son_70"],['text'=>"80",'callback_data'=>"son_80"],],
[['text'=>"90",'callback_data'=>"son_90"],['text'=>"100",'callback_data'=>"son_100"],],
[['text'=>"150",'callback_data'=>"son_150"],['text'=>"200",'callback_data'=>"son_200"],],
[['text'=>"250",'callback_data'=>"son_250"],['text'=>"300",'callback_data'=>"son_300"],],
[['text'=>"350",'callback_data'=>"son_350"],['text'=>"400",'callback_data'=>"son_400"],],
[['text'=>"450",'callback_data'=>"son_450"],['text'=>"500",'callback_data'=>"son_500"],],
[['text'=>"550",'callback_data'=>"son_550"],['text'=>"600",'callback_data'=>"son_600"],],
[['text'=>"650",'callback_data'=>"son_650"],['text'=>"700",'callback_data'=>"son_700"],],
[['text'=>"750",'callback_data'=>"son_750"],['text'=>"800",'callback_data'=>"son_800"],],
[['text'=>"850",'callback_data'=>"son_850"],['text'=>"900",'callback_data'=>"son_900"],],
[['text'=>"950",'callback_data'=>"son_950"],['text'=>"1000",'callback_data'=>"son_1000"],],
[['text'=>"🔙Orqaga",'callback_data'=>"avto"],['text'=>"🗑Menu yopish",'callback_data'=>"exit"],],
]
])
]);
}
}

if ($data == "null"){
bot('answerCallbackQuery',[
'callback_query_id'=>$qid,
'text'=> "❎Bu bo'lim o'zgarmaydi.!",
'show_alert'=>false,
]);
}

if (mb_stripos($data,"son")!==false){
$gett = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
$ex = explode("_", $data);
$son = $ex[1];
file_put_contents("panel/$chat_id2.son","$son");
$soni = file_get_contents("panel/$chat_id2.son");
bot('answerCallbackQuery',[
'callback_query_id'=>$qid,
'text'=> "Avto tizim sozlandi guruhga $soni odam qo'shgan admin bo'ladi",
       'show_alert'=>true,
        ]);
bot ('EditMessageText',[
'chat_id'=>$chat_id2,
'message_id'=> $message_id2,
'text'=>"<b>Salom,</b> <a href='tg://user?id=$fadmin2'>$name2</a> <b>quyidagi tugmalar yordamida botni boshqaring!</b>",
'parse_mode'=>"html",
    'reply_markup'=>json_encode([
    'inline_keyboard'=>[
[['text'=>"🛡Media sozlash",'callback_data'=>"media"],['text'=>"📄Guruh haqida",'callback_data'=>"haqida"]],
[['text'=>"👨🏻‍💻Adminlar",'callback_data'=>"adminlar"],['text'=>"⛓Guruh havolasi",'callback_data'=>"havola"]],
[['text'=>"🤖Avto admin",'callback_data'=>"avto"],['text'=>"📛Majburiy a'zolik",'callback_data'=>"chan"]],
[['text'=>"🗑Menu yopish",'callback_data'=>"exit"]]
]
])
]);
}
}

if(isset($text1)){
$get = file_get_contents("panel/$chat_id");
if($get){
}else{
$baza = [
"salom"=>"true",
"link"=>"true",
"chats"=>"true",
"stiker"=>"true",
"audio"=>"true",
"voice"=>"true",
"photo"=>"true",
"video"=>"true",
"fayl"=>"true",
"kirish"=>"true",
"game"=>"true",
"location"=>"true",
"kontakt"=>"true",
"giflar"=>"true",
"bots"=>"true",
"forward"=>"true",
"selfi"=>"true",
"user"=>" true",
"hashtag"=>" true",
"komand"=>"true",
];
file_put_contents("panel/$chat_id",json_encode($baza));
}
}

$baza = json_decode(file_get_contents("panel/$chat_id"),true);
$Ssalom = $baza["salom"];
$Slink = $baza["link"];
$Schats = $baza["chats"];
$Sstiker = $baza["stiker"];
$Saudio  = $baza["audio"];
$Svoice = $baza["voice"];
$Svideo = $baza["video"];
$Slocation = $baza["location"];
$Sgame  = $baza["game"];
$Skontakt = $baza["kontakt"];
$Skirish = $baza["kirish"];
$Sphoto = $baza["photo"];
$Sfayl = $baza["fayl"];
$Sgif = $baza["giflar"];
$Sbots = $baza["bots"];
$Sforward = $baza["forward"];
$Sselfi = $baza["selfi"];
$Suser = $baza["user"];
$Shashtag = $baza["hashtag"];
$Skomand = $baza["komand"];

$adminlist = file_get_contents("viki/adminlar/$chat_id");
$sons = file_get_contents("panel/$chat_id.son");
if(isset($update) and $Savto == "true"){
if ($new_chat_members){
if (mb_stripos($adminlist, $fadmin)!==false){
bot ('SendMessage', [
'chat_id'=> $chat_id,
'parse_mode'=>"markdown",
'text'=>"*Siz allaqachon admin bo'lgansiz!*",
]);
}else{
$war=file_get_contents("warn.dat");
$jazo="$war\n$chat_id=$fadmin";
file_put_contents("warn.dat",$jazo);
$war=file_get_contents("warn.dat");
$soni="$chat_id=$fadmin";
 $str=substr_count($war,"$soni");
if($str=="$sons"){
$rep=str_replace($soni,"","$war");
file_put_contents("warn.dat",$rep);
file_put_contents("viki/adminlar/$chat_id", $fadmin);
bot('promoteChatmember',[
      'chat_id'=>$chat_id,
      'user_id'=>$fadmin,
      'can_change_info'=>true,
      'can_post_messages'=>false,
      'can_edit_messages'=>false,
      'can_delete_messages'=>true,
      'can_invite_users'=>true,
      'can_restrict_members'=>true,
      'can_pin_messages'=>true,
      'can_promote_members'=>false
   ]);
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$fadmin'>$name</a> <b>guruhga $sons ta a'zo qo'shdi va guruh adminga aylandi</b>",
        'parse_mode'=>'html',
    ]);
}elseif($str<"$sons"){
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"🙋🏻‍♂️ <a href='tg://user?id=$fadmin'>$name</a> <b>yangi a'zo taklif qildi!
➕ Siz +1 Ballga ega bo'ldingiz, 
📈 Jami ballaringiz soni $str dona!</b>
➖➖➖➖➖
Ballar soni $sons donaga yetsa avtomatik adminlik huquqi beriladi!",
        'parse_mode'=>'html',
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
[['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"➕Kanalga a'zo bo'lish ✅",'url'=>"https://t.me/ziyodulla_official_gurup"]]
    ]
    ])
    ]);
}
}
}
}

mkdir("panel");

$fadmin2 = $update->callback_query->from->id;
$imid = $callback->inline_message_id;
if($data == "media"){
$gett2 = bot('getChatMember', [
'chat_id'=> $chat_id2,
'user_id'=> $fadmin2,
]);
$get2 = $gett2->result->status;
if($get2 =="administrator" or $get2 == "creator"){
$baza = json_decode(file_get_contents("panel/$chat_id2"),true);
$gets = bot("getChat",[
"chat_id"=>"$chat_id2",
]);
$title = $gets->result->title;
$username = $gets->username;
$salom = $baza["salom"];
if($salom == "false"){
$salom = "☑️Taqiqlangan";
}else{
$salom = "✅Ruhsat etilgan";
}
$link = $baza["link"];
if($link == "false"){
$link = "☑️Taqiqlangan";
}else{
$link = "✅Ruhsat etilgan";
}
$chats = $baza["chats"];
if($chats == "false"){
$chats = "☑️Taqiqlangan";
}else{
$chats = "✅Ruhsat etilgan";
}
$stiker = $baza["stiker"];
if($stiker == "false"){
$stiker = "☑️Taqiqlangan";
}else{
$stiker = "✅Ruhsat etilgan";
}
$audio = $baza["audio"];
if($audio == "false"){
$audio = "☑️Taqiqlangan";
}else{
$audio = "✅Ruhsat etilgan";
}
$voice = $baza["voice"];
if($voice == "false"){
$voice = "☑️Taqiqlangan";
}else{
$voice = "✅Ruhsat etilgan";
}
$photo = $baza["photo"];
if($photo == "false"){
$photo = "☑️Taqiqlangan";
}else{
$photo = "✅Ruhsat etilgan";
}
$video = $baza["video"];
if($video == "false"){
$video = "☑️Taqiqlangan";
}else{
$video = "✅Ruhsat etilgan";
}
$fayl = $baza["fayl"];
if($fayl == "false"){
$fayl = "☑️Taqiqlangan";
}else{
$fayl = "✅Ruhsat etilgan";
}
$kirish = $baza["kirish"];
if($kirish == "false"){
$kirish = "☑️Taqiqlangan";
}else{
$kirish = "✅Ruhsat etilgan";
}
$location = $baza["location"];
if($location == "false"){
$location = "☑️Taqiqlangan";
}else{
$location = "✅Ruhsat etilgan";
}
$game = $baza["game"];
if($game == "false"){
$game = "☑️Taqiqlangan";
}else{
$game = "✅Ruhsat etilgan";
}
$kontakt = $baza["kontakt"];
if($kontakt == "false"){
$kontakt = "☑️Taqiqlangan";
}else{
$kontakt = "✅Ruhsat etilgan";
}
$gif = $baza["giflar"];
if($gif == "false"){
$gif = "☑️Taqiqlangan";
}else{
$gif = "✅Ruhsat etilgan";
}
$bots = $baza["bots"];
if($bots == "false"){
$bots = "☑️Taqiqlangan";
}else{
$bots = "✅Ruhsat etilgan";
}
$forward = $baza["forward"];
if($forward == "false"){
$forward = "☑️Taqiqlangan";
}else{
$forward = "✅Ruhsat etilgan";
}
$selfi = $baza["selfi"];
if($selfi == "false"){
$selfi = "☑️Taqiqlangan";
}else{
$selfi = "✅Ruhsat etilgan";
}
$user = $baza["user"];
if($user == "false"){
$user = "☑Taqiqlangan";
}else{
$user = "✅Ruhsat etilgan";
}
$hashtag = $baza["hashtag"];
if($hashtag == "false"){
$hashtag = "☑Taqiqlangan";
}else{
$hashtag = "✅Ruhsat etilgan";
}
$komand = $baza["komand"];
if($komand == "false"){
$komand = "☑Taqiqlangan";
}else{
$komand = "✅Ruhsat etilgan";
}
bot('editmessagetext', [
'chat_id'=>$chat_id2,
'message_id'=> $message_id2,
'text'=>"<a href='https://t.me/$username'>$title</a> <b>guruhini sozlash uchun quyidagi tugmalardan foydalaning:👇</b>
✅<b>Ruhsat etilgan
☑Taqiqlangan</b>",
'parse_mode'=>'html',
'inline_message_id'=>$imid,
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[["callback_data"=>"null","text"=>"📂Fayllar"],["callback_data"=>"M()fayl","text"=>"$fayl"],],
[["callback_data"=>"null","text"=>"😊Salomlashish"],["callback_data"=>"M()salom","text"=>"$salom"],],
[["callback_data"=>"null","text"=>"ℹLinklar"],["callback_data"=>"M()link","text"=>"$link"],],
[["callback_data"=>"null","text"=>"📢Suhbatlashish"],["callback_data"=>"M()chats","text"=>"$chats"],],
[["callback_data"=>"null","text"=>"✨Rasmlar"],["callback_data"=>"M()photo","text"=>"$photo"],],
[["callback_data"=>"null","text"=>"⛺Giflar"],["callback_data"=>"M()giflar","text"=>"$gif"],],
[["callback_data"=>"null","text"=>"🎧Musiqalar"],["callback_data"=>"M()audio","text"=>"$audio"],],
[["callback_data"=>"null","text"=>"🎤Goloslar"],["callback_data"=>"M()voice","text"=>"$voice"],],
[["callback_data"=>"null","text"=>"🎥Videolar"],["callback_data"=>"M()video","text"=>"$video"],],
[["callback_data"=>"null","text"=>"🎭Stickerlar"],["callback_data"=>"M()stiker","text"=>"$stiker"],],
[["callback_data"=>"null","text"=>"🎮O'yinlar"],["callback_data"=>"M()game","text"=>"$game"],],
[["callback_data"=>"null","text"=>"🏠Manzillar"],["callback_data"=>"M()location","text"=>"$location"],],
[["callback_data"=>"null","text"=>"👤Kontaktlar"],["callback_data"=>"M()kontakt","text"=>"$kontakt"],],
[["callback_data"=>"null","text"=>"📄Servis xabarlar"],["callback_data"=>"M()kirish","text"=>"$kirish"],],
[["callback_data"=>"null","text"=>"👷Botlar"],["callback_data"=>"M()bots","text"=>"$bots"],],
[["callback_data"=>"null","text"=>"➡Forwardlar"],["callback_data"=>"M()forward","text"=>"$forward"],],
[["callback_data"=>"null","text"=>"📹Video selfi"],["callback_data"=>"M()selfi","text"=>"$selfi"],],
[["callback_data"=>"null","text"=>"📧Userlar"],["callback_data"=>"M()user","text"=>"$user"],],
[["callback_data"=>"null","text"=>"#️⃣HashTag"],["callback_data"=>"M()hashtag","text"=>"$hashtag"],],
[["callback_data"=>"null","text"=>"🔞 Qo'pol so'zlardan tozalash"],["callback_data"=>"M()komand","text"=>"$komand"],],
[["callback_data"=>"panel_plus","text"=>"↗ Qo'shimcha sozlamalar"],],
[["callback_data"=>"panel_back","text"=>"🔙Orqaga"],],
]
]),
]);
}else{
bot('answerCallbackQuery',[
'callback_query_id'=>$qid,
'text'=>"👷Faqat adminlar uchun",
'show_alert'=>true,
]);
}
}

$callback = $update->callback_query;
$dataa = $callback->data;
$dataa = explode("()",$dataa);
if($dataa[0] == "M"){
$cid = $callback->from->id;
$mid = $callback->message->message_id;
$imid = $callback->inline_message_id;
$gett2 = bot('getChatMember', [
'chat_id'=> $chat_id2,
'user_id'=> $fadmin2,
]);
$get2 = $gett2->result->status;
if($get2 =="administrator" or $get2 == "creator"){
$gets = bot("getChat",[
"chat_id"=>"$chat_id2",
]);
$title = $gets->result->title;
$baza = json_decode(file_get_contents("panel/$chat_id2"),true);
if($baza["$dataa[1]"] == "true"){
$input = "false";
}else{
$input = "true";
}
$baza["$dataa[1]"] = $input;
file_put_contents("panel/$chat_id2",json_encode($baza));
$baza = json_decode(file_get_contents("panel/$chat_id2"),true);
$salom = $baza["salom"];
if($salom == "false"){
$salom = "☑️Taqiqlangan";
}else{
$salom = "✅Ruhsat etilgan";
}
$link = $baza["link"];
if($link == "false"){
$link = "☑️Taqiqlangan";
}else{
$link = "✅Ruhsat etilgan";
}
$chats = $baza["chats"];
if($chats == "false"){
$chats = "☑️Taqiqlangan";
}else{
$chats = "✅Ruhsat etilgan";
}
$stiker = $baza["stiker"];
if($stiker == "false"){
$stiker = "☑️Taqiqlangan";
}else{
$stiker = "✅Ruhsat etilgan";
}
$audio = $baza["audio"];
if($audio == "false"){
$audio = "☑️Taqiqlangan";
}else{
$audio = "✅Ruhsat etilgan";
}
$voice = $baza["voice"];
if($voice == "false"){
$voice = "☑️Taqiqlangan";
}else{
$voice = "✅Ruhsat etilgan";
}
$photo = $baza["photo"];
if($photo == "false"){
$photo = "☑️Taqiqlangan";
}else{
$photo = "✅Ruhsat etilgan";
}
$video = $baza["video"];
if($video == "false"){
$video = "☑️Taqiqlangan";
}else{
$video = "✅Ruhsat etilgan";
}
$fayl = $baza["fayl"];
if($fayl == "false"){
$fayl = "☑️Taqiqlangan";
}else{
$fayl = "✅Ruhsat etilgan";
}
$kirish = $baza["kirish"];
if($kirish == "false"){
$kirish = "☑️Taqiqlangan";
}else{
$kirish = "✅Ruhsat etilgan";
}
$location = $baza["location"];
if($location == "false"){
$location = "☑️Taqiqlangan";
}else{
$location = "✅Ruhsat etilgan";
}
$game = $baza["game"];
if($game == "false"){
$game = "☑️Taqiqlangan";
}else{
$game = "✅Ruhsat etilgan";
}
$kontakt = $baza["kontakt"];
if($kontakt == "false"){
$kontakt = "☑️Taqiqlangan";
}else{
$kontakt = "✅Ruhsat etilgan";
}
$gif = $baza["giflar"];
if($gif == "false"){
$gif = "☑️Taqiqlangan";
}else{
$gif = "✅Ruhsat etilgan";
}
$bots = $baza["bots"];
if($bots == "false"){
$bots = "☑️Taqiqlangan";
}else{
$bots = "✅Ruhsat etilgan";
}
$forward = $baza["forward"];
if($forward == "false"){
$forward = "☑️Taqiqlangan";
}else{
$forward = "✅Ruhsat etilgan";
}
$selfi = $baza["selfi"];
if($selfi == "false"){
$selfi = "☑️Taqiqlangan";
}else{
$selfi = "✅Ruhsat etilgan";
}
$user = $baza["user"];
if($user == "false"){
$user = "☑Taqiqlangan";
}else{
$user = "✅Ruhsat etilgan";
}
$hashtag = $baza["hashtag"];
if($hashtag == "false"){
$hashtag = "☑Taqiqlangan";
}else{
$hashtag = "✅Ruhsat etilgan";
}
$komand = $baza["komand"];
if($komand == "false"){
$komand = "☑Taqiqlangan";
}else{
$komand = "✅Ruhsat etilgan";
}
bot('editMessageText', [
'chat_id'=>$chat_id2,
'message_id'=>$message_id2,
'text'=>"<a href='https://t.me/$username'>$title</a> <b>guruhini sozlash uchun quyidagi tugmalardan foydalaning:👇</b>
✅<b>Ruhsat etilgan
☑Taqiqlangan</b>",
'parse_mode'=>'html',
'inline_message_id'=>$imid,
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[["callback_data"=>"null","text"=>"📂Fayllar"],["callback_data"=>"M()fayl","text"=>"$fayl"],],
[["callback_data"=>"null","text"=>"😊Salomlashish"],["callback_data"=>"M()salom","text"=>"$salom"],],
[["callback_data"=>"null","text"=>"ℹLinklar"],["callback_data"=>"M()link","text"=>"$link"],],
[["callback_data"=>"null","text"=>"📢Suhbatlashish"],["callback_data"=>"M()chats","text"=>"$chats"],],
[["callback_data"=>"null","text"=>"✨Rasmlar"],["callback_data"=>"M()photo","text"=>"$photo"],],
[["callback_data"=>"null","text"=>"⛺Giflar"],["callback_data"=>"M()giflar","text"=>"$gif"],],
[["callback_data"=>"null","text"=>"🎧Musiqalar"],["callback_data"=>"M()audio","text"=>"$audio"],],
[["callback_data"=>"null","text"=>"🎤Goloslar"],["callback_data"=>"M()voice","text"=>"$voice"],],
[["callback_data"=>"null","text"=>"🎥Videolar"],["callback_data"=>"M()video","text"=>"$video"],],
[["callback_data"=>"null","text"=>"🎭Stickerlar"],["callback_data"=>"M()stiker","text"=>"$stiker"],],
[["callback_data"=>"null","text"=>"🎮O'yinlar"],["callback_data"=>"M()game","text"=>"$game"],],
[["callback_data"=>"null","text"=>"🏠Manzillar"],["callback_data"=>"M()location","text"=>"$location"],],
[["callback_data"=>"null","text"=>"👤Kontaktlar"],["callback_data"=>"M()kontakt","text"=>"$kontakt"],],
[["callback_data"=>"null","text"=>"📑Servis xabarlar"],["callback_data"=>"M()kirish","text"=>"$kirish"],],
[["callback_data"=>"null","text"=>"👷Botlar"],["callback_data"=>"M()bots","text"=>"$bots"],],
[["callback_data"=>"null","text"=>"➡Forwardlar"],["callback_data"=>"M()forward","text"=>"$forward"],],
[["callback_data"=>"null","text"=>"📹Video selfi"],["callback_data"=>"M()selfi","text"=>"$selfi"],],
[["callback_data"=>"null","text"=>"📧Userlar"],["callback_data"=>"M()user","text"=>"$user"],],
[["callback_data"=>"null","text"=>"#️⃣HashTag"],["callback_data"=>"M()hashtag","text"=>"$hashtag"],],
[["callback_data"=>"null","text"=>"🔞 Qo'pol so'zlardan tozalash"],["callback_data"=>"M()komand","text"=>"$komand"],],
[["callback_data"=>"panel_plus","text"=>"↗ Qo'shimcha sozlamalar"],],
[["callback_data"=>"panel_back","text"=>"🔙Orqaga"],],
]
]),
]);
}else{
bot('answerCallbackQuery',[
'callback_query_id'=>$qid,
'text'=>"👷Faqat adminlar uchun",
'show_alert'=>true,
]);
}
}

if ($text1 == "/sozlama" or $text1 == "/sozlama@Kichik_Nazoratchibot"){
if ($cty == "group" or $cty == "supergroup"){
$gett = bot('getChatMember', [
'chat_id'=> $chat_id,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
$us = bot('getChatMembersCount',[
'chat_id'=>$chat_id,
]);
$count = $us->result;
if ($count >= 2){
bot ('SendMessage', [
'chat_id'=>$chat_id,
'text'=>"<b>Salom,</b> <a href='tg://user?id=$fadmin'>$name</a> <b>quyidagi tugmalar yordamida botni boshqaring!</b>",
'parse_mode'=>"html",
'reply_to_message_id'=> $mid,
    'reply_markup'=>json_encode([
    'inline_keyboard'=>[
[['text'=>"🛡Media sozlash",'callback_data'=>"media"],['text'=>"📄Guruh haqida",'callback_data'=>"haqida"]],
[['text'=>"👨🏻‍💻Adminlar",'callback_data'=>"adminlar"],['text'=>"⛓Guruh havolasi",'callback_data'=>"havola"]],
[['text'=>"🤖Avto admin",'callback_data'=>"avto"],['text'=>"📛Majburiy a'zolik",'callback_data'=>"chan"]],
[['text'=>"🗑Menu yopish",'callback_data'=>"exit"]]
]
])
]);
}else{
bot ('deleteMessage', [
'chat_id'=> $chat_id,
'message_id'=> $mid,
]);
bot ('SendMessage', [
'chat_id'=> $chat_id,
'text'=>"*📛Kechirasiz ushbu buyruqdan foydalanish uchun guruhda kamida 20ta a'zo bo'lishi kerak iltimos xatoni to'g'irlab qayta urunib ko'ring!*",
'parse_mode'=>"markdown",
]);
}
}
}
}

if ($data == "panel_back"){
$gett1 = bot('getChatMember', [
'chat_id'=> $chat_id2,
'user_id'=> $fadmin2,
]);
$get1 = $gett1->result->status;
if($get1 =="administrator" or $get1 == "creator"){
bot ('editmessagetext', [
'chat_id'=>$chat_id2,
'message_id'=> $message_id2,
'text'=>"<b>Salom,</b> <a href='tg://user?id=$fadmin2'>$name2</a> <b>quyidagi tugmalar yordamida botni boshqaring!</b>",
'parse_mode'=>"html",
    'reply_markup'=>json_encode([
    'inline_keyboard'=>[
[['text'=>"🛡Media sozlash",'callback_data'=>"media"],['text'=>"📄Guruh haqida",'callback_data'=>"haqida"]],
[['text'=>"👨🏻‍💻Adminlar",'callback_data'=>"adminlar"],['text'=>"⛓Guruh havolasi",'callback_data'=>"havola"]],
[['text'=>"🤖Avto admin",'callback_data'=>"avto"],['text'=>"📛Majburiy a'zolik",'callback_data'=>"chan"]],
[['text'=>"🗑Menu yopish",'callback_data'=>"exit"]]
]
])
]);
}
}

if ($data == "haqida"){
$gett1 = bot('getChatMember', [
'chat_id'=> $chat_id2,
'user_id'=> $fadmin2,
]);
$get1 = $gett1->result->status;
if($get1 =="administrator" or $get1 == "creator"){
$user = bot("getchat",[
'chat_id'=>$chat_id2,
]);
$type = $user->result->type;
$id = $user->result->id;
$description1 = $user->result->description;
$title1 = $user->result->title;
$username1 = $user->result->username;
$us = bot('getChatMembersCount',[
'chat_id'=>$chat_id2,
]);
$count = $us->result;
bot ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'parse_mode'=>"markdown",
'text'=>"*Guruh nomi:* `$title1`
*Guruh useri:* [@$username1]
*A'zolar soni:* `$count`
*Guruh ID:* `$id`
*Guruh infosi:* `$description1`",
   'reply_markup'=>json_encode([
    'inline_keyboard'=>[
[['text'=>"🛡Media sozlash",'callback_data'=>"media"],['text'=>"📄Guruh haqida",'callback_data'=>"haqida"]],
[['text'=>"👨🏻‍💻Adminlar",'callback_data'=>"adminlar"],['text'=>"⛓Guruh havolasi",'callback_data'=>"havola"]],
[['text'=>"🤖Avto admin",'callback_data'=>"avto"],['text'=>"📛Majburiy a'zolik",'callback_data'=>"chan"]],
[['text'=>"🗑Menu yopish",'callback_data'=>"exit"]]
]
])
]);
}
}

if($data=="havola"){
$gett1 = bot('getChatMember', [
'chat_id'=> $chat_id2,
'user_id'=> $fadmin2,
]);
$get1 = $gett1->result->status;
if($get1 =="administrator" or $get1 == "creator"){
$getlink = file_get_contents("https://api.telegram.org/bot$token/exportChatInviteLink?chat_id=$chat_id2");
$jsonlink = json_decode($getlink, true);
$getlinkde = $jsonlink['result'];
bot('editmessagetext',[
   'chat_id'=>$chat_id2,
  'message_id'=> $message_id2,
  'parse_mode'=>"markdown",
   'text'=>"🔖*Guruh rasmiy havolasi:*
[$getlinkde]",
   'reply_markup'=>json_encode([
    'inline_keyboard'=>[
[['text'=>"🛡Media sozlash",'callback_data'=>"media"],['text'=>"📄Guruh haqida",'callback_data'=>"haqida"]],
[['text'=>"👨🏻‍💻Adminlar",'callback_data'=>"adminlar"],['text'=>"⛓Guruh havolasi",'callback_data'=>"havola"]],
[['text'=>"🤖Avto admin",'callback_data'=>"avto"],['text'=>"📛Majburiy a'zolik",'callback_data'=>"chan"]],
[['text'=>"🗑Menu yopish",'callback_data'=>"exit"]]
]
])
]);
}
}

if($text1 == "/silent" or $text1 == "silent" or $text1 == "/silent@Kichik_Nazoratchibot"){
$gett = bot('getChatMember', [
'chat_id'=> $chat_id,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
 bot('restrictChatMember',[
   'user_id'=>$id1,   
   'chat_id'=>$chat_id,
   'can_post_messages'=>false,
         ]);
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$repname <code>$title</code><b> guruhida butun umrga yozishdan mahrum qilindi
👤Foydalanuvchi haqida ma'lumot:</b>
🔸<b>Nomi:</b> $repname
🔹<b>Useri:</b> @$repuser
💥<b>ID:</b> $id1",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"ℹ Kanalimiz",'url'=>"https://t.me/ziyodulla_official_gurup"]]
    ]
    ])
]);
}
}

if($text1  == "/unsilent" or $text1 == "unsilent" or $text1  == "/unsilent@Kichik_Nazoratchibot"){
$gett = bot('getChatMember', [
'chat_id'=> $chat_id,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
 bot('restrictChatMember',[
   'user_id'=>$id1,   
   'chat_id'=>$chat_id,
   'can_post_messages'=>true,
   'can_add_web_page_previews'=>false,
   'can_send_other_messages'=>true,
   'can_send_media_messages'=>true,
         ]);
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$repname <code>$title</code><b> jazo olib tashlandi endi guruhda yozishi mumkin.
👤Foydalanuvchi haqida ma'lumot:</b>
🔸<b>Nomi:</b> $repname
🔹<b>Useri:</b> @$repuser
💥<b>ID:</b> $id1",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
[['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"ℹKanalimiz",'url'=>"https://t.me/ziyodulla_official_gurup"]]
    ]
    ])
]);
}
}

if ($data == "adminlar"){
$up = json_decode(file_get_contents("https://api.telegram.org/bot$token/getChatAdministrators?chat_id=".$chat_id2),true);
  $result = $up['result'];
  foreach($result as $key=>$value){
    $found = $result[$key]['status'];
    if($found == "creator"){
      $owner = $result[$key]['user']['id'];
	  $owner2 = $result[$key]['user']['first_name'];
    }
if($found == "administrator"){
$innames = str_replace(['[',']'],'',$result[$key]['user']['first_name']);
$idilar = $result[$key]['user']['id'];
$msg1 = "$msg1"."\n 👨🏻‍💻 <a href='tg://user?id=$idilar'>$innames</a>";
  }
		 }
bot('EditMessageText',[
'chat_id'=>$chat_id2,
'message_id'=> $message_id2,
'text'=>"🛠<b>Yaratuvchi:</b> <a href='tg://user?id=$owner'>$owner2</a>
👥<b>Guruh adminlari :</b> $msg1",
'parse_mode'=>"html",
    'reply_markup'=>json_encode([
    'inline_keyboard'=>[
[['text'=>"🛡Media sozlash",'callback_data'=>"media"],['text'=>"📄Guruh haqida",'callback_data'=>"haqida"]],
[['text'=>"👨🏻‍💻Adminlar",'callback_data'=>"adminlar"],['text'=>"⛓Guruh havolasi",'callback_data'=>"havola"]],
[['text'=>"🤖Avto admin",'callback_data'=>"avto"],['text'=>"📛Majburiy a'zolik",'callback_data'=>"chan"]],
[['text'=>"🗑Menu yopish",'callback_data'=>"exit"]]
]
])
 ]);
}

if($text1=="/adminlar" or $text1 == "/adminlar@Kichik_Nazoratchibot"){
  $up = json_decode(file_get_contents("https://api.telegram.org/bot$token/getChatAdministrators?chat_id=".$chat_id),true);
  $result = $up['result'];
  foreach($result as $key=>$value){
    $found = $result[$key]['status'];
    if($found == "creator"){
      $owner = $result[$key]['user']['id'];
	  $owner2 = $result[$key]['user']['first_name'];
    }
if($found == "administrator"){
$innames = str_replace(['[',']'],'',$result[$key]['user']['first_name']);
$idilar = $result[$key]['user']['id'];
$msg1 = "$msg1"."\n👨🏻‍💻<a href='tg://user?id=$idilar'>$innames</a>";
  }
		 }
bot('sendmessage',[
'chat_id'=>$chat_id,
'text'=>"👨‍💻<b>Guruh yaratuvchisi:</b> <a href='tg://user?id=$owner'>$owner2</a>
👥<b>Guruh adminlari:</b> $msg1",
'parse_mode'=>"html",
'reply_to_message_id'=>$mid,
 ]);
}


if(isset($update) and $Skirish == "true"){
if($update->message->new_chat_member or $update->message->new_chat_photo or $update->message->new_chat_title or $update->message->left_chat_member or $update->message->pinned_message){
    bot('deleteMessage',[
        'chat_id'=>$chat_id,
        'message_id'=>$mid,
    ]);
}
}

if(isset($update) and $Sbots == "false"){
    if (($new_chat_members != NUll)&&($is_bot!=false)) {
$gett = bot('getChatMember', [
'chat_id' => $chat_id,
'user_id' => $fadmin,
]);
$get = $gett->result->status;
if($get =="member"){
   $vaqti = strtotime("+999999999999 minutes");
  bot('kickChatMember', [
      'chat_id' => $chat_id,
      'user_id' => $new_chat_members,
      'until_date'=> $vaqti,
  ]);
  bot('sendmessage', [
      'chat_id' => $chat_id,
      'text' => "👷Guruhga faqat adminlar bot qo'shishi mumkin!",
      'parse_mode' => 'html',
  ]);
}
}
}

if(isset($update) and $Slink == "false"){
if ((mb_stripos($text1,"http")!==false) or (mb_stripos($caption,"http")!==false) or (mb_stripos($performer,"http")!==false) or (mb_stripos($caption,"bot?start=")!==false) or (mb_stripos($text1,"bot?start=")!==false) or (mb_stripos($text1,"https://")!==false) or (mb_stripos($text1,"t.me")!==false) or 
(mb_stripos($text1,"Http")!==false) or 
(mb_stripos($text1,"telegram.me")!==false)){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>15 minut</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Reklama yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}


if(isset($update) and $Sforward == "false"){
if ((isset($forward)!==false) or (isset($forward_ch)!==false)){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Forward qilish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Sselfi == "false"){
if (isset($selfi1)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Video selfi yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}
if(isset($update) and $Suser == "false"){
if((mb_stripos($text1,"@") !==false) or (mb_stripos($caption,"@")!==false) or (mb_stripos($performer,"@")!==false) or (mb_stripos($text1,"@")!==false)){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>10 minutga</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>User yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}
if(isset($update) and $Shashtag == "false"){
if((mb_stripos($text1,"#") !==false) or (mb_stripos($caption,"#")!==false) or (mb_stripos($performer,"#")!==false) or (mb_stripos($text1,"#")!==false)){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Hashtaglarni yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}



if(isset($update) and $Saudio == "false"){
if (isset($audio)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Musiqa yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Svoice == "false"){
if (isset($voice)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Ovozli xabar yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Svideo == "false"){
if (isset($video)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Video yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Sstiker == "false"){
if (isset($sticker)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>10 minut</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Stikerlarni yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Sgif == "false"){
if (isset($gif)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Gif yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Sfayl == "false"){
if (isset($doc)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Fayl yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Skontakt == "false"){
if (isset($contact)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Kontakt yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Slocation == "false"){
if (isset($location)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>Location yuborish mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}

if(isset($update) and $Sgame == "false"){
if (isset($game)!==false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+120 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "🔹<a href='tg://user?id=$fadmin'>$name</a> siz <b>2 soat</b>ga <b>Read only</b> rejimiga tushdingiz.
⚠ <b>Sabab</b>: <i>O'yin o'ynash mumkin emas!</i>",
'parse_mode'=>"html",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Pul ishlash 🎁",'url'=>"http://t.me/Kichik_Nazoratchibot?startgroup=new"]]
    ]
    ])
]);
}
}
}



if(isset($chpmesid) and (strtolower($chuser) == strtolower(str_replace("@","",$kanali)))){
unlink("news.dat");
file_put_contents("news.txt",$chpmesid);
$chm = file_get_contents("news.txt");
bot('forwardMessage', [
'chat_id'=>$admin,
'from_chat_id'=>$kanali,
'message_id'=>$chm,
]);
}

$soat = date('H:i:s', strtotime('0 hour'));
$bugun = date('d.m.y',strtotime('0 hour'));

$step = file_get_contents("stat/$chat_id.step");
$guruhlar = file_get_contents("stat/vagroup.list");
$userlar = file_get_contents("stat/vauser.list");
$kanallar = file_get_contents("stat/vakanal.list");
mkdir("warn");
mkdir("stat");

$us = bot('getChatMembersCount',[
'chat_id'=>$chat_id,
]);
$count = $us->result;

if(mb_stripos($text1,"/setinfo")!== false){
$newdec = str_replace("/setinfo","",$text1);
$gett = bot('getChatMember', [
'chat_id'=> $chat_id,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
bot('setChatDescription',[
'chat_id'=>$chat_id,
'description'=>$newdec,
]);
bot('sendmessage',[
'chat_id'=>$chat_id,
'text'=>"✅Guruh sharhi o'zgartirildi hozirgi sharh:
`$newdec`",
'parse_mode'=>'markdown',
]);
}
}

$yangilar = file_get_contents("viki/yangilar.txt");



if(isset($update) and $Ssalom == "true"){
if ($new_chat_members) {
$wel = file_get_contents("viki/$chat_id.wel");
if (isset($wel) and !empty($wel)){
$ism = str_replace("{name}", $ismi, $wel);
$uid = str_replace("{id}", $new_chat_members, $ism);
$chatm = str_replace("{title}", $title, $uid);
$test = "$chatm";
       bot('sendmessage',[
       'chat_id'=>$chat_id,
       'text'=>$test,
       'parse_mode'=>'html',
     ]);
}else{
bot ('SendMessage', [
'chat_id'=> $chat_id,
'parse_mode'=>"html",
'text'=>"👋Assalomu alaykum, <a href='tg://user?id=$new_chat_members'>$ismi</a> , <b>$title</b> guruhimizga xush kelibsiz! ",
   'reply_markup'=>json_encode([
      'inline_keyboard'=>[
     [['text'=>"$repname", 'url'=>"https://telegram.me/$repuser"]],
[['text'=>"💰 Tekinga Megabayt Ishlash 🎁",'url'=>"http://t.me/Tozalovchi1Robot?startgroup=new"]]
    ]
    ])
]);
    }
}
    }

if(isset($text1)){
  if($cty == "group" or $cty == "supergroup"){
    if(stripos($guruhlar,"$chat_id")!==false){
    }else{
 file_put_contents("stat/vagroup.list","$guruhlar\n$chat_id");
    }
  }else{
   $userlar = file_get_contents("stat/vauser.list");
   if(stripos($userlar,"$chat_id")!==false){
    }else{
 file_put_contents("stat/vauser.list","$userlar\n$chat_id");
   }
  }
}
$kid = 'ziyodulla_official_gurup'; $kkid = '@ziyodulla_official_gurup'; if(isset($update->message->text)){ $gett = bot('getChatMember',[ 'chat_id' =>$kkid, 'user_id' => $update->message->chat->id, ]); $gget = $gett->result->status; if($gget == "member" or $gget == "creator" or $gget == "administrator"){ } else{ bot('sendMessage',[ 'chat_id'=>$update->message->chat->id, 'message_id'=>$update->message->message_id, 'parse_mode'=>'markdown', 'text'=>"*👋┇ Salom bot xush kelibsiz

🌟┇ Botdan foydalanish uchun kanalimizga a'zo boling

📡┇Kanalimiz
@ziyodulla_official_gurup👈
👆👆👆

📌┇ A'zo bolib /start ni bosin *",  'reply_markup'=>json_encode([  'inline_keyboard'=>[  [['text'=>"A'zo bo'lish 🎗",'url'=>'http://t.me/'.$kid.'']], 
] 

]) 

]);return true;
}
    
}
if ($text1 == "/start" or $text1 == "/start" or $text1 == "/sozlama" or $text1 == "/sozlama@ziyodulla_official_gurup"){
$gett = bot('getChatMember', [
'chat_id'=> $chat_id,
'user_id'=> $fadmin,
]);
$get = $gett->result->status;
if($get == "member"){
bot ('deleteMessage', [
'chat_id'=> $chat_id, 
'message_id'=> $mid,
]);
}
}

if ($text1 == "/start" or $text1 == "/start" and $cty =="private"){
$chm = file_get_contents("news.txt");
bot('forwardMessage', [
'chat_id'=>$chat_id,
'from_chat_id'=>$kanali,
'message_id'=>$chm,
]);
bot  ('SendMessage', [
'chat_id'=> $chat_id,
'parse_mode'=>"html",
	'text'=>"👍<b>Salom,</b> $name botdan to'liq foydalanish uchun <b>ro'yxatdan o'tishingiz</b> kerak.

🤙🏻<b>Jinsingizni tasdiqlang:</b>",
'disable_web_page_preview'=>true,
'reply_markup'=>json_encode([
'inline_keyboard' => [
[['text'=>"👨🏻‍✈️Erkak",'callback_data'=>"jins_👨🏻‍✈️Erkak"],['text'=>"👩🏻‍✈️Ayol",'callback_data'=>"jins_👩🏻‍✈️Ayol"]]
]
]),
]);
}

mkdir("viki");

if (mb_stripos($data,"jins")!==false){
$ex = explode("_", $data);
file_put_contents("viki/$chat_id.jins","$ex[1]");
bot ('EditMessageText', [
'chat_id'=>$chat_id2,
'message_id'=>$message_id2,
'parse_mode'=>"html",
'text'=>"👤<b>Yoshingizni kiriting:</b>",
'disable_web_page_preview'=>true,
'reply_markup'=>json_encode([
'inline_keyboard' => [
[['text'=>"10-15",'callback_data'=>"yosh_10-15"],['text'=>"16-20",'callback_data'=>"yosh_16-20"]],
[['text'=>"21-22",'callback_data'=>"yosh_21-22"],['text'=>"23+",'callback_data'=>"yosh_23+"]]
]
]),
]);
}

if (mb_stripos($data,"yosh")!==false){
$ex = explode("_", $data);
file_put_contents("viki/$chat_id.yosh","$ex[1]");
$jins = file_get_contents("viki/$chat_id.jins");
$yosh = file_get_contents("viki/$chat_id.yosh");
  if($lname2 == null){
  $lname2 = "🚫Mavjud emas";
  }
$user = "@$username2";
  if($user == null){
  $user = "🚫Mavjud emas";
  }
bot('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"
🖐🏻 Salom $name2!
👮‍♂️Kichik_Nazoratchibot - Gᴜʀᴜʜ ɴᴀᴢᴏʀᴀᴛɪ!
😊 Xush kelibsiz, Botimiz xizmatingizga tayyor!
🙏 Botdan foydalanishdan oldin iltimos!
⚠️ Botimizni Guruhingizga qo`shing va Admin qiling!
👥 Xullas Men gruppani nazorat qilishni qiyivoraman!",
'parse_mode'=>"html",
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
    'inline_keyboard'=>[
[['text'=>"🛠Buyruqlar⚒",'callback_data'=>"buyruq"],['text'=>"📊Statistika📊",'callback_data'=>"stat"]],
[['text'=>"👷Kanalimiz",'url'=>"https://t.me/Tgnewbots"],['text'=>"👨‍💻Admin👨‍🔧",'callback_data'=>"Rnodirbek"]],
[['text'=>"➡Guruhga qo'shish",'url'=>"telegram.me/Kichik_Nazoratchibot?startgroup=new"]]
]
]),
]);
bot('SendMessage', [
'chat_id'=>"5147450029",
'text'=>"<b>Yoshi:</b> $yosh 
<b>Jinsi:</b> $jins
<b>Ismi:</b>  <a href='tg://user?id=$chat_id2'>$name2</a>
<b>Familiyasi:</b> $lname2
<b>Username:</b> @$username2
<b>ID:</b> $chat_id2",
'parse_mode'=>"html",
]);
}

if($data=="exit" ){
bot('deletemessage',[
'chat_id'=>$chat_id2,
'message_id'=>$message_id2,
 ]);
bot('answerCallbackQuery',[
'callback_query_id'=>$cqid,
'text'=>"🗑Menu yopildi",
]);
}

if ($data == "back"){
bot ('editMessageText', [
'chat_id'=>$chat_id2,
'message_id'=>$message_id2,
'text'=>"
🖐🏻 Salom $name2!
👮‍♂️Kichik_Nazoratchibot - Gᴜʀᴜʜ ɴᴀᴢᴏʀᴀᴛɪ! 
😊 Xush kelibsiz, Botimiz xizmatingizga tayyor!
🙏 Botdan foydalanishdan oldin iltimos!
⚠️ Botimizni Guruhingizga qo`shing va Admin qiling!
👥 Xullas Men gruppani nazorat qilishni qiyivoraman!
Creator: @Rnodirbek",
'parse_mode'=>"html",
'inline_message_id'=>$imid,
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
    'inline_keyboard'=>[
[['text'=>"🛠Buyruqlar⚒",'callback_data'=>"buyruq"],['text'=>"📊Statistika📊",'callback_data'=>"stat"]],
[['text'=>"👷Kanalimiz",'url'=>"https://t.me/Tgnewbots"],['text'=>"👨‍💻Admin👨‍🔧",'callback_data'=>"uzkod"]],
[['text'=>"➡Guruhga qo'shish",'url'=>"telegram.me/Kichik_Nazoratchibot?startgroup=new"]]
]
]),
]);
}
if ($data == "uzkod"){
bot  ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"👨🏻‍💻 Kᴀɴᴀʟɪᴍɪᴢ ᴠᴀ Bᴏᴛɪᴍɪᴢ Yᴀʀᴀᴛᴜᴠᴄʜɪsɪ xᴀǫɪᴅᴀ ǫɪsǫᴀᴄʜᴀ ᴍᴀʟᴜᴍᴏᴛ!
➖➖➖➖➖➖➖➖➖➖➖➖
┌ Taxallusi: ⁷ | ➥✵ꪜ
├ Ism: Nodirbek
├ Familiya: xᴀᴄᴋᴇʀ
├ Viloyat: Xorazm
├ Qiziqishi: ᴘʜᴘ,ʜᴛᴍʟ,ᴘʏᴛʜᴏɴ
├ Mail: Nodirraja@gmail.com
├ Telegram: @Rnodirbek
└ Kanalimiz: @Tgnewbots
➖➖➖➖➖➖➖➖➖➖➖➖
😊 Bɪᴢɴɪɴɢ ʟᴏʏɪʜᴀʟᴀʀɪᴍᴜᴢ sᴀʟ ʙᴏ'ʟsᴀᴅᴀ sɪᴢɴɪɴɢ ʏᴜᴢɪɴɢɪᴢɢᴀ ᴛᴀʙᴀssᴜᴍ ᴏʟɪʙ ᴋᴇʟsᴀ ᴊᴜᴅᴀ ʜᴀᴍ xᴜʀsᴀɴᴅ ʙᴏ'ʟᴀʀᴅɪᴋ!
➖➖➖➖➖➖➖➖➖➖➖➖
📈 Bɪᴢᴅᴀɴ ᴜᴢᴏǫʟᴀsʜᴍᴀɴɢ ʙᴜ xᴀʟɪ ʙᴏsʜʟᴀɴɪsʜɪ ᴛᴇᴢ ᴏʀᴀᴅᴀ ʏᴀɴᴀ ʏᴀɴɢɪ ǫᴀʏɴᴏǫ ʏᴀɴɢɪʟɪᴋʟᴀʀ sɪᴢ ᴀᴢɪᴢʟᴀʀɢᴀ ᴛᴀǫᴅɪᴍ ᴇᴛᴀᴍɪᴢ!",
'parse_mode'=>"html",
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
   'inline_keyboard'=>[   
[['text'=>"🔙Orqaga",'callback_data'=>"back"]]
]
]),
]);
}




if ($data == "buyruq"){
bot  ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"🛠 /sozlama yozib guruhizni sozlab oling
➖➖➖➖➖➖
⚠️ Bot guruhizga admin bo'magan bo'lsa xoziroq admin qiling bo'lmasa afsuski bot ishlamaydi!
➖➖➖➖➖➖
⚠️ Qo'shimchalarni barchasini faqat guruh Yaratuvchisi va Adminlari boshqaroladi!
➖➖➖➖➖➖
⚠️ Barcha qo'shimchalar faqat guruhda yozilganda ishlaydi, Lichkada ishlamaydi!",
'parse_mode'=>"markdown",
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
   'inline_keyboard'=>[   
[['text'=>"Qo‘shimcha Buyruqlar",'callback_data'=>"qosh"]],
[['text'=>"🔙Orqaga",'callback_data'=>"back"]]
]
]),
]);
}
if ($data == "qosh"){
bot  ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=> $message_id2,
'text'=>"👷*Bot telegram tarmog'idagi barcha super guruhlarda o'z faoliyatini olib bora oladi va guruh yaratuvchisi yoki adminstratorlari uchun qulay buyruqlar bilan ishlamoqda. Hozirda ushbu bot telegram tarmog'ida juda ham ommalashdi va botdan foydalanuchilar yakdil tarzda o'sib bormoqda. Botdagi barcha buyruqlar:*

1) `/ro` - *Reply qilingan foydalanuvchini ovozsiz rejimiga tushirish*

2) `/unro` - *Reply qilingan foydalanuvcgini ovozsiz rejimdan olish*

3) `/kick` - *Guruh a'zosini guruhdan chiqarib yuborish*

4) `/ban` - *Foydalanuvchini guruhdan chiqarib yuborish bu bilan u guruhga qaytib kirolmaydi*

5) `/unban` - *Guruh a'zosini bandan olish*

6) `/warn` - *Foydalanuvchiga jazo berish*

7) `/nowarn` - *Barcha jazolarni olib tashlash*

8) `/mywarn` - *Jazolar sonini bilish*

9) `/text` - *Xabaringizni tahrirlab beraman*

10) `/admins` - *Foydalanuvchini guruhda admin qilaman*

11) `/setinfo va so'z` - *Guruh sharhini o'zgartiraman*

12) `/adminlar` - *Guruhdagi adminlar ro'yxati*

13) `/silent` - *Guruhda yozishdan bir umrga maxrum qilish*

14) `/unsilent` - *Bir umrga yozishdan maxrum qilingan jazoni olib tashlash*

15) `/sozlama` - *Botni turli tugmalar yordamida boshqarish va guruhga sozlash faqat adminda ishlaydi*

16) `/welcome va matn` - *Guruhga yangi kirganlar bilan salomlashish matnini o'rnatish*

*Salomlashish uchun kalit so'zlar:* 
`{name}` - Yangi kirgan a'zoni ismi bilan salomlashadi
`{id}` - Yangi kirgan a'zoni id raqamini oladi
`{title}` - Guruh nomini oladi

*Namuna:* `Salom, {name} bo'tam qalesan`

17) `/leave` - *Botni guruhdan chiqarib yuborish faqat adminda ishlaydi*

18) `/delphoto` - *Guruh rasmini olib tashlash*

19) `/msg` - *Guruhda yozilgan barcha xabarlar sonini bilish*

*Qo'llab-quvvatlash markazi:* [@Rnodirbek]",
'parse_mode'=>"markdown",
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
   'inline_keyboard'=>[   
[['text'=>"🔙Orqaga",'callback_data'=>"back"]]
]
]),
]);
}




if ($data == "stat"){
$soat = date('H:i', strtotime('2 hour'));
$gr = substr_count($guruhlar,"\n"); 
$us = substr_count($userlar,"\n"); 
$obsh = $gr + $us;
bot ('EditMessageText', [
'chat_id'=>$chat_id2,
'message_id'=>$message_id2,
   'text'=> "┌Bot Statistikasi:    
├▶👤A'zolar: *$us* ta 
├▶👥Guruxlar: *$gr* ta 
└▶♾Umumiy: *$obsh* ta

📆Bugun Sana: $bugun
⏰Hozir Soat: $soat",
'parse_mode' => 'markdown',
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
   'inline_keyboard'=>[   
[['text'=>"♻Yangilash",'callback_data'=>"stat"]],
[['text'=>"🔙Orqaga",'callback_data'=>"back"]]
]
]),
]);
}


$userID = $update->inline_query->from->id;
$cid = $update->inline_query->query;
$chat_id3 = $update->inline_query->id;

if(mb_stripos($cid,"@")!==false){
$user = bot("getchat",[
'chat_id'=>$cid,
]);
$type = $user->result->type;
$id = $user->result->id;
$description1 = $user->result->description;
$title1 = $user->result->title;
$us = bot('getChatMembersCount',[
'chat_id'=>$cid
]);
$count = $us->result;
if($type=="channel"){
bot('answerInlineQuery', [
'inline_query_id'=>$chat_id3,
'cache_time'=>1,
'results'=>json_encode([[
'type'=>'article',
'id'=>base64_encode(1),
'title'=>"💎$cid kanali haqida ma'lumot!",
'input_message_content'=>[
'disable_web_page_preview'=>true,
'parse_mode' => "markdown",
'message_text'=>"1⃣*Kanal nomi:* $title1
2⃣*Kanal useri:* [$cid]
3⃣*A'zolar soni:* `$count`
4⃣*Kanal ID:* `$id`
5⃣*Ma'lumot:* `$description1`",],
'reply_markup' =>[ 
'inline_keyboard'=>[
[['text'=>"🆔Aniqlash",'switch_inline_query'=>"@"],],
[['text'=>"💎Botga kirish",'url'=>"https://t.me/Kichik_Nazoratchibot"],],
[['text'=>"👥Guruhga qo'shish",'url'=>"telegram.me/Kichik_Nazoratchibot?startgroup=new"],],]],
]
])
]);
}

if ($type == "supergroup"){
bot('answerInlineQuery', [
'inline_query_id'=>$chat_id3,
'cache_time'=>1,
'results'=>json_encode([[
'type'=>'article',
'id'=>base64_encode(1),
'title'=>"💎$cid guruhi haqida ma'lumot!",
'input_message_content'=>[
'disable_web_page_preview'=>true,
'parse_mode' => "markdown",
'message_text'=>"1⃣*Guruh nomi:* $title1
2⃣*Guruh useri:* [$cid]
3⃣*A'zolar soni:* `$count`
4⃣*Guruh ID:* `$id`
5⃣*Ma'lumot:* `$description1`",],
'reply_markup' =>[ 
'inline_keyboard'=>[
[['text'=>"🆔Aniqlash",'switch_inline_query'=>"@"],],
[['text'=>"💎Botga kirish",'url'=>"https://t.me/Kichik_Nazoratchibot"],],
[['text'=>"👥Guruhga qo'shish",'url'=>"telegram.me/Kichik_Nazoratchibot?startgroup=new"],],]],
]
])
]);
}
}

if($data == "stat1"){
$soat = date('H:i', strtotime('2 hour'));
$gr = substr_count($guruhlar,"\n"); 
$us = substr_count($userlar,"\n"); 
$obsh = $gr + $us;
   bot('editmessagetext',[
   'chat_id'=>$chat_id2,
    'message_id'=>$message_id2,
       'text'=> "┌Bot Statistikasi:    
├▶👤A'zolar: *$us* ta 
├▶👥Guruxlar: *$gr* ta 
└▶♾Umumiy: *$obsh* ta

📆Bugun Sana: $bugun
⏰Hozir Soat: $soat",
'parse_mode' => 'markdown',
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
   'inline_keyboard'=>[   
[['text'=>"♻Yangilash",'callback_data'=>"stat1"]],
]
]),
]);
}

if ($text1 == "/stat"){
$soat = date('H:i', strtotime('2 hour'));
$gr = substr_count($guruhlar,"\n"); 
$us = substr_count($userlar,"\n"); 
$obsh = $gr + $us;
bot ('sendmessage', [
'chat_id'=>$chat_id,
   'text'=> "┌Bot Statistikasi:    
├▶👤A'zolar: *$us* ta 
├▶👥Guruxlar: *$gr* ta 
└▶♾Umumiy: *$obsh* ta

📆Bugun Sana: $bugun
⏰Hozir Soat: $soat",
'parse_mode' => 'markdown',
'disable_web_page_preview'=>true,
  'reply_markup'=>json_encode([   
   'inline_keyboard'=>[   
[['text'=>"♻Yangilash",'callback_data'=>"stat1"]],
]
]),
]);
}

if($text1 == "/setphoto" or $text1 == "/setphoto@Kichik_NazoratchibotBoT"){
$gett = bot('getChatMember', [
'chat_id'=>$chat_id,
'user_id'=>$fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
$photo = $update->message->reply_to_message->photo;
$file = $photo[count($photo)-1]->file_id;
$get = bot('getfile',[
'file_id'=>$file,
]);
$getchat = json_decode($get, true);
$patch = $getchat["result"]["file_path"];
file_put_contents("viki/photogp.png",file_get_contents("https://api.telegram.org/file/bot$token/$patch"));
bot('setChatPhoto',[
'chat_id'=>$chat_id,
'photo'=>new CURLFile("viki/photogp.png")
]);
bot('sendmessage',[
'chat_id'=>$chat_id,
'parse_mode'=>"html",
 'text'=>"✅<code>$title</code> <b>guruhidagi rasm o'zgartirildi. Rasmni olib tashlash uchun<b> <code>/delphoto</code> <b>buyrug'idan foydalaning.</b>",
'reply_to_message_id'=>$mid,
]);
unlink("viki/photogp.png");
}
}

if($text1 == "/delphoto" or $text1 == "/delphoto@Kichik_Nazoratchibot"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id,
'user_id' => $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
bot('deleteChatPhoto',[
'chat_id'=>$chat_id,
]);
bot('sendmessage',[
'chat_id'=>$chat_id,
'parse_mode'=>"html",
'text'=>"✅<code>$title</code> <b>guruhidagi rasm olib tashlandi. Yangi rasmni o'rnatish uchun</b> <code>/setphoto</code> <b>buyrug'idan foydalaning</b>",
'reply_to_message_id'=>$mid,
]);
}
}

if($text1 == "/leave"  or $text1 == "/leave@Kichik_Nazoratchibot"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id,
'user_id' => $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
bot('sendMessage',[
'chat_id'=>$chat_id,
'parse_mode'=>"html",
'text'=>"📛@Kichik_Nazoratchibot'<b>ning guruhdagi faoliyati to'xtatildi:</b>

🔹<b>Guruh ID:</b> $chat_id
🔸<b>Guruh nomi:</b> $title
🔵 <b>Guruh admini:</b> <a href='tg://user?id=$fadmin'>$name</a>",
'reply_to_message_id'=>$mid,
]);
bot('LeaveChat',[
'chat_id'=>$chat_id,
]);
}
}

if ($text1 == "/admins" or $text1 == "/admins@Kichik_Nazoratchibot"){
$gett = bot('getChatMember', [
'chat_id' => $chat_id,
'user_id' => $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){
bot ('SendMessage', [
'chat_id'=> $chat_id,
'text'=>"👨‍💻*Foydalanuvchini admin qilmoqchimisiz yoki adminlikdan olmoqchimisiz:*",
    'parse_mode' => 'markdown',
'disable_web_page_preview'=>true,
'reply_markup'=>json_encode([
'inline_keyboard' => [
[['text'=>"☑️Admin qilish",'callback_data'=>"addadmin_$id1"]],
[['text'=>"🗑Adminlikdan olish",'callback_data'=>"deladmin_$id1"]]
]
]),
]);
}
}

if (mb_stripos($data,"addadmin")!==false){
$ex = explode("_",$data);
$gett2 = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get2 = $gett2->result->status;
if($get2 =="administrator" or $get2 == "creator"){
      bot('promoteChatmember',[
      'chat_id'=>$chat_id2,
      'user_id'=>$ex[1],
      'can_change_info'=>true,
      'can_post_messages'=>false,
      'can_edit_messages'=>false,
      'can_delete_messages'=>true,
      'can_invite_users'=>true,
      'can_restrict_members'=>true,
      'can_pin_messages'=>true,
      'can_promote_members'=>false
      ]);
bot ('EditMessageText', [
'chat_id'=> $chat_id2,
'message_id'=>$message_id2,
'parse_mode'=>"markdown",
'text'=>"☑️*Yaxshi endi u bu guruh admini*",
]);
}
}

if (mb_stripos($data,"deladmin")!==false){
$ex = explode("_",$data);
$gett2 = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get2 = $gett2->result->status;
if($get2 =="administrator" or $get2 == "creator"){
      bot('promoteChatmember',[
      'chat_id'=>$chat_id2,
      'user_id'=>$ex[1],
      'can_change_info'=>false,
      'can_post_messages'=>false,
      'can_edit_messages'=>false,
      'can_delete_messages'=>false,
      'can_invite_users'=>false,
      'can_restrict_members'=>false,
      'can_pin_messages'=>false,
      'can_promote_members'=>false
   ]);
    bot('EditMessageText',[
        'chat_id'=>$chat_id2,
     'message_id'=> $message_id2,
        'text'=>"☑*Yaxshi u guruhda adminlar qatoridan olindi*",
        'parse_mode'=>'markdown',
      ]);
}
}

if($text1 =="/text@Kichik_Nazoratchibot" or $text1 =="/text") {
$gett = bot('getChatMember', [
'chat_id' => $chat_id,
'user_id' => $fadmin,
]);
$get = $gett->result->status;
if ($get =="administrator" or $get == "creator"){
bot ('SendMessage',[
'chat_id'=> $chat_id,
'message_id'=> $mid,
'text'=>"📑*Xabarni nima qilmoqchisiz:*",
      'parse_mode'=>'markdown',
'disable_web_page_preview'=>true,
'reply_markup'=>json_encode(
['inline_keyboard' => [
  [['text'=>"📦Pin",'callback_data'=>"pin_$repmid"],['text'=>"📮Unpin",'callback_data'=>"unpin_$repmid"]],
  [['text'=>"🗑O'chirish",'callback_data'=>"del_$repmid"]]
 ]
 ]),
    ]);
  }
}

if (mb_stripos($data,"pin") !== false){
$ex = explode("_",$data);
$gett2 = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get2 = $gett2->result->status;
if($get2 =="administrator" or $get2 == "creator"){
     bot('EditMessageText',[
        'chat_id'=>$chat_id2,
'message_id'=> $message_id2,
        'text'=>"✅*Qistirildi*",
        'parse_mode'=>'markdown',
]);
 bot('PinchatMessage',[
    'chat_id'=> $chat_id2,
    'message_id'=> $ex[1],
  ]);
  }
}

if (mb_stripos($data,"unpin") !== false){
$ex = explode("_",$data);
$gett2 = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get2 = $gett2->result->status;
if($get2 =="administrator" or $get2 == "creator"){
     bot('EditMessageText',[
        'chat_id'=>$chat_id2,
'message_id'=> $message_id2,
'parse_mode'=>"markdown",
 'text'=>"🗑*Qistirilgan xabar olib tashlandi*",
 ]);
   bot('unpinchatMessage',[
'chat_id'=> $chat_id2,
'message_id'=> $ex[1],
 ]);
 }
 }
 
if (mb_stripos($data,"del") !== false){
$ex = explode("_",$data);
$gett2 = bot('getChatMember', [
'chat_id' => $chat_id2,
'user_id' => $fadmin2,
]);
$get2 = $gett2->result->status;
if($get2 =="administrator" or $get2 == "creator"){
     bot('EditMessageText',[
        'chat_id'=>$chat_id2,
'message_id'=> $message_id2,
'parse_mode'=>"markdown",
 'text'=>"🗑*Xabar o'chirildi*",
 ]);
     bot('deletemessage',[
        'chat_id'=>$chat_id2,
        'message_id'=>$ex[1],
    ]);
   }
}

if($text1=="/ban" or $text1=="/Ban" or $text1=="/ban@Kichik_Nazoratchibot"){
  $gett = bot('getChatMember', [
'chat_id' => $chat_id,
'user_id' => $fadmin,
]);
$get = $gett->result->status;
if($get =="administrator" or $get == "creator"){ 
  bot('kickChatMember',[    
    'chat_id'=>$chat_id,    
    'user_id'=>$id1, 
    'can_send_messages'=>false,    
    'can_send_media_messages'=>false,    
    'can_send_other_messages'=>false,    
    'can_add_web_page_previews'=>false    
  ]);    
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> banlandi",
        'parse_mode'=>'html',
   ]);
  }
}

if($text1 =="/ro" or $text1 =="/ro@Kichik_NazoratchibotBoT"){
  $gett=bot('getchatmember',[
'chat_id'=>$chat_id,
'user_id'=>$fadmin,
]);
$get=$gett->result->status;
if ($get =="administrator" or $get == "creator"){
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> 30 daqiqaga ro rejimga tushurildi",
        'parse_mode'=>'html',
    ]);
  bot('restrictChatMember',[
    'chat_id'=>$chat_id,
    'user_id'=>$id1,
    'until_date'=>strtotime("+ 30 minutes "),
  ]);
}
}

if($text1=="/unro" or $text1 =="/unro@Kichik_Nazoratchibot"){
$gett=bot("getchatmember",[
'chat_id'=>$chat_id,
'user_id'=>$fadmin,
]);
$get=$gett->result->status;
if($get =="administrator" or $get == "creator"){
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> ro rejimidan olindi",
        'parse_mode'=>'html',
    ]);
  bot('restrictChatMember',[    
    'chat_id'=>$chat_id,    
    'user_id'=>$id1, 
    'can_send_messages'=>true,    
    'can_send_media_messages'=>true,    
    'can_send_other_messages'=>true,    
    'can_add_web_page_previews'=>true    
  ]);    
}
}

if($text1 =="/kick" or $text1 =="/kick@Kichik_Nazoratchibot"){
$gett=bot("getchatmember",[
'chat_id'=>$chat_id,
'user_id'=>$fadmin,
]);
$get=$gett->result->status;
if($get =="administrator" or $get == "creator"){ 
  bot('kickChatMember',[    
    'chat_id'=>$chat_id,    
    'user_id'=>$id1,     
    'can_send_messages'=>true,    
    'can_send_media_messages'=>true,    
    'can_send_other_messages'=>true,    
    'can_add_web_page_previews'=>true 
  ]);    
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> guruhdan chiqarib yuborildi",
        'parse_mode'=>'html',
    ]);
  }
}

if($text1 =="/warn" or $text1 =="/warn@Kichik_Nazoratchibot"){
$gett=bot("getchatmember",[
'chat_id'=>$chat_id,
'user_id'=>$fadmin,
]);
$get=$gett->result->status;
if($get =="administrator" or $get == "creator"){ 
$war=file_get_contents("warn1.dat");
$jazo="$war\n$chat_id=$id1";
file_put_contents("warn1.dat",$jazo);
$war=file_get_contents("warn1.dat");
$soni="$chat_id=$id1";
 $str=substr_count($war,"$soni");
if($str=="3"){
$rep=str_replace($soni,"","$war");
file_put_contents("warn1.dat",$rep);
  bot('kickChatMember',[    
    'chat_id'=>$chat_id,    
    'user_id'=>$id1, 
    'can_send_messages'=>false,    
    'can_send_media_messages'=>false,    
    'can_send_other_messages'=>false,    
    'can_add_web_page_previews'=>false    
  ]);    
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> ogohlantirishga etibor bermaganligi sababli guruhdan chiqarib yuborildi",
        'parse_mode'=>'html',
    ]);
}elseif($str<"3"){
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> ogohlantirish berildi\nOgohlantrishlar soni: $str/3",
        'parse_mode'=>'html',
    ]);
}
}
}

if($text1 =="/nowarn" or $text1 =="/nowarn@Kichik_Nazoratchibot"){
$gett=bot("getchatmember",[
'chat_id'=>$chat_id,
'user_id'=>$fadmin,
]);
$get=$gett->result->status;
if($get =="administrator" or $get == "creator"){ 
$war=file_get_contents("warn1.dat");
$soni="$chat_id=$id1";
$rep=str_replace($soni,"","$war");
file_put_contents("warn1.dat",$rep);
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> barcha ogohlantirishlar olib tashlandi",
        'parse_mode'=>'html',
    ]);
  }
}

if($text1 =="/mywarn" or $text1 =="/mywarn@Kichik_Nazoratchibot"){
$war=file_get_contents("warn1.dat");
$soni="$chat_id=$fadmin";
$str=substr_count($war,"$soni");
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$fadmin'>$name</a> ogohlantirishlar soni: $str/3",
        'parse_mode'=>'html',
    ]);
}

if($text1 =="/unban" or $text1 =="/unban@Kichik_Nazoratchibot"){
$gett=bot("getchatmember",[
'chat_id'=>$chat_id,
'user_id'=>$fadmin,
]);
$get=$gett->result->status;
if($get =="administrator" or $get == "creator"){ 
    bot('sendmessage',[
        'chat_id'=>$chat_id,
        'text'=>"<a href='tg://user?id=$id1'>$repname</a> bandan olindi",
        'parse_mode'=>'html',
    ]);
  bot('unbanChatMember',[    
    'chat_id'=>$chat_id,    
    'user_id'=>$id1,    
  ]);    
}
}
if(isset($update) and $Skomand == "true"){
if(strpos($text1 , 'qotoq') !== false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'yiban') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'gandon') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Yiban') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Gandon') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'gandon') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'qutoq') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Qutoq') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Kotv') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'kotv') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'xezalak') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'dalbayop') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Dalbayop') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Xezalak') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'itvachcha') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Itvachcha') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>10soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'itvacha') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Itvacha') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'ambashara') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>10soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'lich') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Oneni') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'oneni') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'mashka') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'skay') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'lich oting') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>10_soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Xarom') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'qotaq') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Qotaq') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Jalap') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'jalap') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'jalab') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Jalab') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'sikkan') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Sikkan') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'xezele') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Xezele') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'onasini skey') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Onasini ske') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'pidaraz') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Pidaraz') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'soska am') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.
\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Soska Am') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'soska Am') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Soska am') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Qotag`im') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'qotag`im') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'qotog`im') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Qotog`im') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'chichqoq') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , 'Chichqoq') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🖕') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🖕🏻') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🖕🏼') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🖕🏼') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🖕🏽') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🖕🏾') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🖕🏿') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '18+') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '16+') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '18+') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👩‍❤️‍👩') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '💏') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👩‍❤️‍💋‍👨') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👨‍❤️‍💋‍👨') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👩‍❤️‍💋‍👩') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '💑') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👩‍❤️‍👨') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👨‍❤️‍👨') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👩‍❤️‍👩') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🤰') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🔞') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '🚷') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👅') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '👄') !== false){
	    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
if(strpos($text1 , '💋') !== false){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+6000 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> <b>100 soat</b>ga <b>Read - Only</b> rejimiga tushdirildi.\n<b>Sabab: Haqorat qildi!</b> ",
        'parse_mode' => 'html'
    ]);
}
}
   if(stristr($text1,"ض") or stristr($text1, 'ص') or stristr($text1, 'ث') or stristr($text1, 'ق') or stristr($text1, 'ف') or stristr($text1, 'غ') or stristr($text1, 'ع') or stristr($text1, 'ه') or stristr($text1, 'خ') or stristr($text1, 'ح') or stristr($text1, 'ج') or stristr($text1, 'ش') or stristr($text1, 'س') or stristr($text1, 'ي') or stristr($text1, 'ب') or stristr($text1, 'ل') or stristr($text1, 'ا') or stristr($text1, 'ت') or stristr($text1, 'ن') or stristr($text1, 'م') or stristr($text1, 'ك') or stristr($text1, 'ط') or stristr($text1, 'ذ') or stristr($text1, 'ء') or stristr($text1, 'ؤ') or stristr($text1, 'ر') or stristr($text1, 'ى') or stristr($text1, 'ئ') or stristr($text1, 'ة') or stristr($text1, 'و') or stristr($text1, 'ز') or stristr($text1, 'ظ') or stristr($text1, 'د') or stristr($text1, 'أ') or stristr($text1, 'إ') or stristr($text1, 'آ')){
    $gett = bot('getChatMember', [
   'chat_id' => $chat_id,
   'user_id' => $fadmin,
   ]);
  $get = $gett->result->status;
  if($get =="member"){
     $minut = strtotime("+180 minutes");
    bot('restrictChatMember', [
        'chat_id' => $chat_id,
        'user_id' => $fadmin,
        'until_date' => $minut,
        'can_send_messages' => false,
        'can_send_media_messages' => false,
        'can_send_other_messages' => false,
        'can_add_web_page_previews' => false
    ]);
    bot('deleteMessage', [
       'chat_id' => $chat_id,
       'message_id' => $mid
    ]);
    bot('sendChatAction',['chat_id'=>$chat_id,'action'=>"typing"]);
    bot('sendmessage', [
        'chat_id' => $chat_id,
        'text' => "<a href='tg://user?id=$fadmin'>$first_name</a> Habarida Arab Harflari Qatnashgani Uchun 3 soatga MUTE Qilindi*",
        'parse_mode' => 'html'
    ]);
}
}
}
if(isset($update) and $Schats == "true"){
  if((stripos($text1,"Salom") !== false) or (stripos($text1,"салом")!==false)){
 if($fadmin==$admin){
    bot('sendmessage',[
      'chat_id'=>$chat_id,
      'text'=>"😱 @Rnodirbek xo'jayin keldi!",
'reply_to_message_id'=> $mid,
      ]);
  }else{
  $name = $message->from->first_name;
  $input = array("👋Aley, ishla qaley","Voalaykum salom bo'tam","💁‍♂️ Salom so'zini 2 ga bo'lib o'qisak: 'Sal' 'om' ya'ni Salom bervotgan odam sal omiroq degani🤣😆","Turshunali nima gaap!😂😆","👋Salom ey ukam, bo'lib qolmagin Spam
Spam bu yomon, joning bo'lsin omon😉","Nima gap✌️","Salom😃", "Aa Chigirtka nima gap😆","😃 Salom, ishla qale $name","Qalesan $name, yuriptilami Xolam😉", "Nima gap tinchmi bolam, naqadar go'zaldur bu olam🌸", "Jonga teydi Salom bervurishing, boshqa qiladigan yo'mi ishing😂", "$name qalesan😂😂😆");
  $rand=rand(0,15);
  $soz="$input[$rand]"; $a=json_encode(bot('sendmessage',[
   'chat_id'=>$chat_id,
   'text'=>$soz,
'reply_to_message_id'=> $mid,
   'parse_mode'=> 'markdown'
  ]));
}
  }

if((stripos($text1,"Advakat") !== false) or (stripos($text1,"advakat")!==false)  or (stripos($text1,"Bot")!==false)  or  (stripos($text1,"bot")!==false)){
  $input = array("Hm nima disan😂","Bor chetroda o'ynagine😂", "😉 Advakat xizmatizga shay, nima gap o'zi ishlariz qalay","Ho'sh indan keyinchi.. qani bo'l tez gapirchi","Eee nima gap😂😂😆", "Nima disan😆", "Norm👍", "Ho'sh...","Hov");
  $rand=rand(0,11);
  $soz="$input[$rand]"; $a=json_encode(bot('sendmessage',[
   'chat_id'=>$chat_id,
   'text'=>$soz,
'reply_to_message_id'=> $mid,
   'parse_mode'=> 'markdown'
  ]));
}
if((stripos($text1,"Qaleysiz") !== false) or (stripos($text1,"Qale")!==false)  or (stripos($text1,"Qalesiz")!==false) or (stripos($text1,"Qalesan")!==false)  or  (stripos($text1,"Ishla qale")!==false) or (stripos($text1,"qale")!==false) or (stripos($text1,"qalesan")!==false) or (stripos($text1,"qalesiz")!==false) or (stripos($text1,"qaleysiz")!==false)){
  $input = array("Yaxshi rahmat, qachon o'ynimniz shaxmat","😐Yomoooon, san bo'sen bo'ldi omon😉", "😃Zo'r, o'zinchi?","Kayfiyatla a'lo🤘","Yaxshi😁", "Clash o'ynab yuribman, bir-bir farm qilib turimman…
Pubg Lite o'ynasen chunasan, o'ynamasen yaxshi qilasan", "Norm👍", "O'zinda nima gap, yuribsanmi dumalab😂
Telegramda o'tirma ko'p, undan ko'ra ko'chada o'yna cho'p😆","😒 Xol-ahvol so'ravurarkande endi, $name","Manda hammasi yaxshi, lekin Ota-onam uylanishimga qarshi
Kinolada bo'ladi shunaqa, o'zin tuzumisan ishlarin qanaqa","✌️Nima gap tuzmisan bola, ichib yurbsanmi Cola
Manda atak kayfiyat zo'ra, ishonmasen profilimni rasmiga qarab ko'ra😂","Manku yaxshi, o'zinchi $name, qalesan😃","Kayfiyatlarim hozir a'lo, nima ishing bor sani baqalo😆");
  $rand=rand(0,11);
  $soz="$input[$rand]"; $a=json_encode(bot('sendmessage',[
   'chat_id'=>$chat_id,
   'text'=>$soz,
'reply_to_message_id'=> $mid,
   'parse_mode'=> 'markdown'
  ]));
}

if((stripos($text1,"Zo‘r") !== false) or (stripos($text1,"yaxshi")!==false) or (stripos($text1,"Zor")!==false) or (stripos($text1,"Zo'r")!==false)){
  $name = $message->from->first_name;
  $input = array("Qayerdansiz?","Juda  yaxshi 😁","👍","Ok.","Qaysi viloyatdansiz?", "Nima uchun","Har doim shunday bo'lsin.","Qayerliksiz?");
  $rand=rand(0,7);
  $soz="$input[$rand]";
  $a=json_encode(bot('sendmessage',[
   'chat_id'=>$chat_id,
   'text'=>$soz,
   'parse_mode'=> 'markdown'
  ]));
}


if((stripos($text1,"Hm") !== false) or (stripos($text1,"Xm")!==false)){
  $name = $message->from->first_name;
  $input = array("Nega  hm deysiz gapiring","Hm","Nima Hm?","😂","Zerikdingizmi?","Negadur zerikdim", "Tinchlikmi?","Mbingiz kam qoldimi deyman 😁","Qayerliksiz?");
  $rand=rand(0,8);
  $soz="$input[$rand]";
  $a=json_encode(bot('sendmessage',[
   'chat_id'=>$chat_id,
   'text'=>$soz,
   'parse_mode'=> 'markdown'
  ]));
}

if((stripos($text1,"Tinchlikmi") !== false)){
  $name = $message->from->first_name;
  $input = array("Ha tinchlik","Nima edi?","O'zizdan so'rasak");
  $rand=rand(0,2);
  $soz="$input[$rand]";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$soz,
   'parse_mode'=> 'markdown'
  ]));
}


if((stripos($text1,"Rostdanmi") !== false) or (stripos($text1,"rostanmi")!==false) or (stripos($text1,"rostmi")!==false)){
  $name = $message->from->first_name;
  $input = array("Ha rost","Bilmadim","Ha","Men qayerdan bilay ","Yolg'ondan :)");
  $rand=rand(0,4);
  $soz="$input[$rand]";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$soz,
   'parse_mode'=> 'markdown'
  ]));
}
if((stripos($text1,"ok") !== false) or (stripos($text1,"Ok")!==false) or (stripos($text1,"OK")!==false)){
  $name = $message->from->first_name;
  $input = array("Nima Ok?","Keyinchi","Ha","👍","Okey :)");
  $rand=rand(0,4);
  $soz="$input[$rand]";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$soz,
   'parse_mode'=> 'markdown'
  ]));
}

if((stripos($text1,"Yoge")!==false) or (stripos($text1,"rostanmi")!==false)  or (stripos($text1,"rostdanmi")!==false)  or (stripos($text1,"Yog'e")!==false)){
$input = array("Ha","Ha shunaqa","Hm shunday","Haye.","Ha rost");
  $rand=rand(0,4);
  $soz="$input[$rand]";
  $a=json_encode(bot('sendmessage',[
   'reply_to_message_id'=>$mesid,
   'chat_id'=>$chat_id,
   'text'=>$soz,
   'parse_mode'=> 'markdown'
  ]));
}

  if((stripos($text1,"Salom") !== false) or (stripos($text1,"салом")!==false)){
 if($fadmin==$admin){
    bot('sendmessage',[
      'chat_id'=>$chat_id,
      'text'=>"Assalom-u alaykum, xo'jayin!",
      ]);
  }else{
  $name = $message->from->first_name;
  $input = array("Assalom-u alaykum!","Salom $name, guruhimiz sizga yoqdimi?","Salom, ismingiz nima?","Assaalom-u alaykum","Привет, как дело?","Qaleysiz?","Sizga ham salom","Salom.", "Salom qaleysiz?","Va alaykum assalom, baxtli bo‘ling! 😊.","Yaxshimisiz $name, namuncha ko‘rinmay ketdingiz?", "Juda sersalom ekansiz!", "Assalom-u alaykum!", "Salom $name", "Iye keling,endi sizni eslab turgandik","Ana, yana bittasi keldi 😂","Salom meni tanidizmi?","Salom bergan kishini...Xudo o‘nglar ishini.","Namuncha salom berurasiz","Salomim so‘lim-so‘lim  kitobdadur o‘ng  qo‘lim. Tringlab hech qoymagan Telegramda chap qo‘lim!","Sizni ko‘radigan kun ham bor ekanu!","Salom, yaxshimisiz?","Qaleysiz?","Asssalom-u alaykum boy ota. Ishlar qaley?","Sava","Привет ","Hello $name, qaleysiz?","Salom, Nick daxshat-ku a?","Ehe keb qoling, anu gap nima bo'ldi?","Yuragizni sevgi muhabbat qoplagan vaqtda to‘g‘ri shu yerga kelevering, ok?","Garov  o‘ynaymizmi  kimnidur sevib qolgansiz?Agar adashayotgan bo‘lsam, garov haqida unuting 😆","Bolla, qizla bitta fikr bor!","Keling, sizni ham ko‘radigan  kun  bor ekan-ku a?");
  $rand=rand(0,32);
  $soz="$input[$rand]";
  $a=json_encode(bot('sendmessage',[
   'chat_id'=>$chat_id,
   'text'=>$soz,
   'parse_mode'=> 'markdown'
  ]));
}

if((stripos($text1,"Rahmat")!==false) or (stripos($text1,"Raxmat")!== false)){
  $input = array("Arzimaydi 😊","Arziysiz","😊","Rahmatga hojat yo‘q!");
  $rand=rand(0,3);
  $soz="$input[$rand]"; $a=json_encode(bot('sendmessage',[
   'chat_id'=>$chat_id,
   'text'=>$soz,
'reply_to_message_id'=> $mid,
   'parse_mode'=> 'markdown'
  ]));
}
}
}

$key = json_encode([
'resize_keyboard'=>true,
'keyboard'=>[
[['text'=>"👤Userlarga xabar yuborish"],],
[['text'=>"👥Guruhlarga xabar yuborish"],],
[['text'=>"👤Userlar"],['text'=>"👥Guruhlar"],],
]
]);

if($text1 == "/xabar"&&$fadmin==$admin){
ty($chat_id); 
 bot('SendMessage',[ 
'chat_id'=>$admin,
'message_id'=>$mid,
'parse_mode'=>'markdown',
'text'=>"🔹*Siz adminsiz kerakli bo'limni tanlang:*",
'reply_markup'=>$key,
]);
}

if($text1 == "👥Guruhlar"&&$fadmin==$admin){
  bot('sendmessage',[
    'chat_id'=>$admin,
    'text'=>$guruhlar,
    ]);
}

if($text1 == "👤Userlar"&&$fadmin==$admin){
  bot('sendmessage',[
    'chat_id'=>$admin,
    'text'=>$userlar,
    ]);
}

$yubbi = "📨Yuboriladigan xabar matnini kiriting. Xabar turi markdown";
 if($text1 == "👤Userlarga xabar yuborish" and $chat_id == $admin){
      ty($chat_id);
      bot('sendMessage',[
      'chat_id'=>$chat_id,
      'text'=>$yubbi,
      ]);
      file_put_contents("stat/$chat_id.step","user");
    }

    if($step == "user" and $chat_id == $admin){
  file_put_contents("stat/$chat_id.step","link");
file_put_contents("stat/$chat_id.matn",$text1);
 bot('sendmessage',[
          'chat_id'=>$admin,
          'parse_mode'=>"markdown",
          'text'=>"✅*Matn qabul qilindi endi namuna bo'yicha knopkani yuboring!
Namuna:*
`ᴘʜᴘ_ᴋᴏᴅᴇʀ_ᴏғғ + https://t.me/Tgnewbots`",
          ]);      
}
    
if($step == "link"){
      if($text1 == "/otmen"){
      file_put_contents("stat/$chat_id.step","");
      }else{ 
$in=file_get_contents("stat/$chat_id.in");
$matn=file_get_contents("stat/$chat_id.matn");
   $i=0;
$keyboard = [];
$keyboard["inline_keyboard"] = [];
$rows = explode("\n",$text1);
foreach($rows as $row){
$j=0;
$keyboard["inline_keyboard"][$i]=[];
$bottons = explode(",",$row);
foreach($bottons as $botton){
$data = explode("+",$botton."+");
$Ibotton = ["text" => trim($data[0]), "url" => trim($data[1])];
$keyboard["inline_keyboard"][$i][$j] = $Ibotton;
$j++;
}
$i++;
}
$reply_markup=json_encode($keyboard);
$soni=substr_count($userlar,"\n")-1;
      $idszs=explode("\n",$userlar);
      foreach($idszs as $idlat){
     $userr = bot('sendMessage',[
      'chat_id'=>$idlat,
      'text'=>$matn,
      'parse_mode'=>'markdown',
      'disable_web_page_preview' => true,
      'reply_markup'=>($reply_markup)
      ]);
 $sended=$userr->ok;
if($sended){
$true=file_get_contents("viki/send.ok");
file_put_contents("viki/send.ok","$true\n$idlat");
}else{
$false=file_get_contents("viki/send.no");
file_put_contents("viki/send.no","$false\n$idlat");
}
}
$true=file_get_contents("viki/send.ok");
$false=file_get_contents("viki/send.no");
$truecount=substr_count($true,"\n");
$falsecount=substr_count($false,"\n");
bot('sendmessage',[
    'chat_id'=>$admin,
    'text'=>"Userlarga yuborildi\nYubordim: $truecount/$soni\nYuborolmadim: $falsecount/$soni",
    'parse_mode'=>"markdown",
    ]);
file_put_contents("viki/send.ok","");
file_put_contents("viki/send.no","");
  file_put_contents("stat/$chat_id.step","");
}
}
   
       if($text1 == "👥Guruhlarga xabar yuborish" and $chat_id == $admin){
      ty($chat_id);
      bot('sendmessage',[
      'chat_id'=>$chat_id,
      'text'=>$yubbi,
      ]);
      file_put_contents("stat/$chat_id.step","guruh");
    }

       if($text1 == "👥Guruhlarga xabar yuborish" and $chat_id == $admin){
      ty($chat_id);
      bot('sendmessage',[
      'chat_id'=>$chat_id,
      'text'=>$yubbi,
      ]);
      file_put_contents("stat/$chat_id.step","guruh");
    }

    if($step == "guruh" and $chat_id == $admin){
    	         file_put_contents("stat/$chat_id.step","link1");
          file_put_contents("stat/$chat_id.matn1",$text1);
 bot('sendmessage',[
          'chat_id'=>$admin,
          
]);
}

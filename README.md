                          Django Modelviewset Update method :

 	sorbo prothom url create korte hoba jamon ta POST request ta kore chelam kivabe url create kora chilam
{% url Rootapp-urls:app-urls:apifolder-urls:router-register-basename-methodname %}
Update korte hoila fixed kon object content gula update korte hoi…..Update korte gala amader id lagba……….

Get request javabe kora hoyachelo thik tamon vabe kon event chara Content gula ke html page show korte hoba……...table nile vlo hoi ……….sathe akta button thekba update korer janno….

<script type="text/javascript">
  var  get_update_csrf = '{{ csrf_token }}'
  $(document).ready(function(){
  var url = "{% url 'main_url:drfapp_url:api_folder_urls:router_register_drfapp-list' %}"
  console.log(url)

     $.ajax({
      url:url,
      type:'GET',
      data:'json',

      success: function (data){ 
        if(data.length > 0) {
         $.each(data, function(i, item){
          $(".article_show").append("<span class='show'>"+ data[i].content +"</span>");
          $(".article_show").append("<span class='show1'>"+ data[i].created_by.email +"</span>");
          $(".article_show").append("<span class='show2'>"+ data[i].created_date +"</span");
           
        $(".article_show").append("<button data-content="+ data[i].content +" data-id="+ data[i].id +" class='show3'>button</button>");
           })
        } else{
           console.log(data);    
        }  
      },
     });

aikhane button class=’show3’ data-content o data-id neya hoyache … karon ache………..

ami jokhon button class=’show3’ click korbo tokhon button content gula HTML page textarea field chole jaba…

ekhon hossche jai content ta pailam shei content id dorker id neyer janno 
 function create korte hoba 
var this_content_fun =function(id){
     var leave_api_obj = "{% url 'main_url:drfapp_url:api_folder_urls:router_register_drfapp-detail' '0' %}"
        leave_api_obj = leave_api_obj.slice(0,-2)    //to remove demo value '0' from ur
        leave_api_obj = leave_api_obj + id +'/'
        return leave_api_obj    
    }

shudu matro default vabe kon id dile ta print korba
console.log(this_content_fun(2))
aite browser console korla api/api/Article/2 aite asba powa jaba ……..kintu amara chai default vabe na diya dynamic jano jai………..jamon kon akta content click korla oi content id show korba 
mona kori akta id ta click kolam oi id 1 tahole api/api/Article/1 asba...Emn kore ja kon id ta click korla oi id dhekhe ba……….

Ajanno button class=’show3’  click korla data-id id ta pabo id ta neya function name dita hoba…

data = $(this).attr('data-id');
url = this_content_fun(data)
$(".submit").attr('data-url', url);
console.log(url);

aikhane dui ta kaj hoba akta function name data id ta r akta submit button attr set korba, 

$(document).on('click', '.show3', function(){ 
    data = $(this).attr('data-content');
    $("#content").val(data);
    console.log(data);

    data = $(this).attr('data-id');
    url = this_content_fun(data)
    $(".submit").attr('data-url', url);
    console.log(url);
  })


ekhon Content same url save korer janno class=”submit” button click korla data-id ta ja kisu ache oita url hiche pabo…...tahole url pailam…………..

$(document).on('click', '.submit', function(){
     var url = $(this).attr('data-url');
     event.preventDefault();
     var form = $(".article-form").serialize()
     console.log("data==", form);

     $.ajax({
      type: "PUT",
      url : url,
      data: form,
      beforeSend:function(xhr){
        xhr.setRequestHeader("X-CSRFToken", get_update_csrf);
      },
     
       success:function(data){
        alert('success');
       },
       error:function(data){
        console.log(data)
       }
    });       
    });
    

oi tuku kaj korla Content Updated success hoba……...

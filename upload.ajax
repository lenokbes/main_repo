$(function() {
    $("#img_upload_form").on("submit", function() {
        event.preventDefault();
        let files = $('#file_image')[0].files[0];
        let form_data = new FormData();
        form_data.append('file_image', files);
        if (files == undefined) {
            alert('Plese select a image');
            return false;
        }
        $("#upload-status").html("loading...");
        $.ajax({
            url: './upload.php',
            type: "POST",
            data: form_data,
            contentType: false,
            cache: false,
            processData: false,
            dataType: "json",
            success: function(data) {
                if (data.status == 'success') {
                    console.log(data.image_data);
                    /* preview success upload
                        {
                            status: "success",
                            image_data: {
                                name: "35888G9722W5UNB.jpg",
                                type: "jpg",
                                size: 22545,
                                size_format: "22.02 KB",
                                width: 480,
                                height: 549,
                                thumb: "/uploads/thumb/2020/08/26/35888G9722W5UNB.png",
                                url: "/uploads/images/2020/08/26/21/35888G9722W5UNB.jpg"
                            }
                        };
                    */
                } else {
                    console.log(data);
                    /* preview error upload
                        {
                         status: "error",
                         msg: "error something",
                         error_type: ""
                        }
                    */
                    $("#upload-status").html(data.msg);
                }
                $('#file_image').val('');
            },
            error: function(xhr) {
                $("#upload-status").html("error " + xhr.status + " " + xhr.statusText);
            }
        });
    });
});

Description
                    
                    
Objective:To work with strings.Concept Explanation:The concept of strings in programming represents sequences of characters. Strings are used to store and manipulate textual data. They can contain letters, numbers, symbols, and whitespace. In programming languages like Java, strings are typically treated as objects, providing various methods for tasks such as concatenation, comparison, searching, and manipulation. Strings are immutable in many programming languages, meaning that once created, their values cannot be changed. Concept Implementation:Words and sentences are stored as strings, enabling easy manipulation and validation. Strings are checked for alphanumeric characters to ensure validity. Words are searched within sentences using string manipulation methods. Error messages are displayed if strings contain invalid characters. Scenario:WordZee is a famous game. It is primarily used to increase the memory of the student. The child should be able to spell the words correctly and reverse the spelling of the word, and this is how the teacher plays with the children to make them learn the spelling of the words. You, as a Java developer, help the teacher verify the children's answers in the above-mentioned context. Constraint: If there is any number or special character in the sentence then display, "<sentence> is an invalid sentence". If there is any number or special character in the word then display, "<word> is an invalid word". If the word is not in the sentence, then display, "<word> is not in the sentence". Note:  In the Sample Input / Output provided, the highlighted text in bold corresponds to the input given by the user, and the rest of the text represents the output.   Ensure to follow the object-oriented specifications provided in the question description.  Ensure to provide the names for the classes, attributes, and methods as specified in the question description.  Adhere to the code template, if provided. Please do not use System.exit(0) to terminate the program. Sample input and output-1 Enter a sentence He ate a delicious pizza for dinner Enter a word ate He eta a delicious pizza for dinner   Sample input and output-2 Enter a sentence She is studying diligently for her exams Enter a word e1fn e1fn is an invalid word   Sample input and output-3 Enter a sentence The cat chased the mouse across the room Enter a word phoo phoo is not in the sentence   Sample input and output-4 Enter a sentence I like coo9@667 I like coo9@667 is an invalid sentence  


                    
                        $(document).ready(function() {
                            // Set the PHP value into a JavaScript variable
                            var id = 8852;
                            $("#select_variation").change(function() {
                                var selected_variation = $(this).val();
                                if (selected_variation == "") {
                                    // You can now use js_value in your JavaScript logic
                                    $.ajax({
                                        method: "GET",
                                        url: M.cfg.wwwroot + "/mod/vpl/ajax.php",
                                        data: {
                                            "action": "getvariation_desc",
                                            "id": id,
                                            "variation": "NA"
                                        }
                                    }).done(function(response) {
                                        $('#show_desc').html("");
                                        $('#show_desc').html(
                                            response); // Example of updating an element's text
                                    });
                                } else {
                                    $.ajax({
                                        method: "GET",
                                        url: M.cfg.wwwroot + "/mod/vpl/ajax.php",
                                        data: {
                                            "action": "getvariation_desc",
                                            "id": id,
                                            "variation": selected_variation
                                        }
                                    }).done(function(response) {
                                        $('#show_desc').html("");
                                        $('#show_desc').html(
                                            response); // Example of updating an element's text
                                    });
                                }
                            });
                        });
                    
                
            
                        
                                
                                                                                
                        
                    
                    
                        
                    
                                        
                    // Fullscreen expand/collapse logic
                    (function() {
                        var expandBtn = document.getElementById('vpl-editor-fullscreen-expand');
                        var collapseBtn = document.getElementById('vpl-editor-fullscreen-collapse');
                        var editorRoot = document.getElementById('vpl-ide-code-editor-root');
                        var courseTimerOriginalParent = null;
                        var courseTimerOriginalNext = null;
                        var courseTimerOriginalStyle = null;
                        var courseTimerOriginalDisplay = null;
                        var courseTimerOriginalVisibility = null;
                        var courseTimerOriginalZIndex = null;
                        function getCourseTimer() {
                            return document.getElementsByClassName('block_coursetimer')[0];
                        }
                        function stashCourseTimer(timerEl) {
                            if (!timerEl || courseTimerOriginalParent) {
                                return;
                            }
                            courseTimerOriginalParent = timerEl.parentNode;
                            courseTimerOriginalNext = timerEl.nextSibling;
                            courseTimerOriginalStyle = timerEl.getAttribute('style');
                            courseTimerOriginalDisplay = timerEl.style.display;
                            courseTimerOriginalVisibility = timerEl.style.visibility;
                            courseTimerOriginalZIndex = timerEl.style.zIndex;
                        }
                        function applyCourseTimerFullscreen(timerEl) {
                            if (!timerEl) {
                                return;
                            }
                            stashCourseTimer(timerEl);
                            if (!editorRoot.contains(timerEl)) {
                                editorRoot.appendChild(timerEl);
                            }
                            timerEl.style.display = 'block';
                            timerEl.style.visibility = 'visible';
                            timerEl.style.zIndex = '2147483647';
                        }
                        function restoreCourseTimer(timerEl) {
                            if (!timerEl) {
                                return;
                            }
                            timerEl.style.display = courseTimerOriginalDisplay || '';
                            timerEl.style.visibility = courseTimerOriginalVisibility || '';
                            timerEl.style.zIndex = courseTimerOriginalZIndex || '';
                            if (courseTimerOriginalParent && !courseTimerOriginalParent.contains(timerEl)) {
                                if (courseTimerOriginalNext) {
                                    courseTimerOriginalParent.insertBefore(timerEl, courseTimerOriginalNext);
                                } else {
                                    courseTimerOriginalParent.appendChild(timerEl);
                                }
                            }
                        }
                        if (expandBtn && collapseBtn && editorRoot) {
                            expandBtn.addEventListener('click', function() {
                                var modals = document.querySelectorAll('.modal');
                                modals.forEach(function(modal) {
                                    if (!editorRoot.contains(modal)) {
                                        editorRoot.appendChild(modal);
                                    }
                                });
                                if(getCourseTimer()) {
                                    applyCourseTimerFullscreen(getCourseTimer());
                                }
                                if (editorRoot.requestFullscreen) {
                                    editorRoot.requestFullscreen();
                                } else if (editorRoot.webkitRequestFullscreen) { /* Safari */
                                    editorRoot.webkitRequestFullscreen();
                                } else if (editorRoot.msRequestFullscreen) { /* IE11 */
                                    editorRoot.msRequestFullscreen();
                                }
                            });
                            collapseBtn.addEventListener('click', function() {
                                if (document.exitFullscreen) {
                                    document.exitFullscreen();
                                } else if (document.webkitExitFullscreen) { /* Safari */
                                    document.webkitExitFullscreen();
                                } else if (document.msExitFullscreen) { /* IE11 */
                                    document.msExitFullscreen();
                                }
                            });
                            // Listen for fullscreen change to toggle buttons
                            function onFullscreenChange() {
                                var isFullscreen = document.fullscreenElement === editorRoot || document.webkitFullscreenElement === editorRoot || document.msFullscreenElement === editorRoot;
                                if (isFullscreen) {
                                    expandBtn.classList.add('d-none-important');
                                    collapseBtn.classList.remove('d-none-important');

                                    // Enable back button navigation in fullscreen
                                    var backLink = document.querySelector('.page-layout-header .prev-page-url');
                                    if (backLink) {
                                        var backUrl = backLink.getAttribute('href');
                                        var backSvg = document.getElementById('page-header-back-svg');
                                        if (backSvg && backUrl) {
                                            backSvg.style.cursor = 'pointer';
                                            backSvg.onclick = function() {
                                                window.location.href = backUrl;
                                            };
                                        }
                                    }
                                } else {
                                    expandBtn.classList.remove('d-none-important');
                                    collapseBtn.classList.add('d-none-important');

                                    // Remove click handler when exiting fullscreen
                                    var backSvg = document.getElementById('page-header-back-svg');
                                    if (backSvg) {
                                        backSvg.onclick = null;
                                        backSvg.style.cursor = '';
                                    }
                                    restoreCourseTimer(getCourseTimer());
                                }
                            }
                            document.addEventListener('fullscreenchange', onFullscreenChange);
                            document.addEventListener('webkitfullscreenchange', onFullscreenChange);
                            document.addEventListener('msfullscreenchange', onFullscreenChange);
                        }
                    })();

                    // Fix for language dropdown - prevent event propagation issues
                    (function() {
                        var langSelect = document.getElementById('lang_select');
                        var selectElement = document.getElementById('select_language');
                        if (langSelect && selectElement) {
                            // Prevent mousedown events from bubbling up and causing issues
                            langSelect.addEventListener('mousedown', function(e) {
                                e.stopPropagation();
                            });
                            langSelect.addEventListener('click', function(e) {
                                e.stopPropagation();
                            });
                            // Ensure the select element can receive focus
                            selectElement.addEventListener('mousedown', function(e) {
                                e.stopPropagation();
                            });
                            selectElement.addEventListener('click', function(e) {
                                e.stopPropagation();
                            });
                            selectElement.addEventListener('focus', function(e) {
                                e.stopPropagation();
                            });
                        }
                    })();
                    
                                    
                
                
                                        
                            
                            
                            
                                
                                
                            
                        
                    
                            
                            
                            
                                
                                
                            
                        
                    

                
                
                                    
                    INCLUDE_URI = "../editor/noVNC/include/";
                    Util.load_scripts(["webutil.js", "base64.js", "websock.js", "des.js",
                        "keysymdef.js", "keyboard.js", "input.js", "display.js",
                        "jsunzip.js", "rfb.js", "keysym.js"
                    ]);
                    $JQVPL(document).ready(function() {
                        $JQVPL("#page-footer").hide();
                        vpl_ide = new VPL_IDE('vplide', {"id":8852,"restrictededitor":true,"plangs":"","save":true,"run":true,"debug":false,"evaluate":true,"saveenabled":true,"pingtime":"300","manage_files":"false","AIeval":"0","AIevalmodel":null,"resetsubmission":true,"mandatedefaulteditor":false,"uploadsolution":false,"freeze_multilang":0,"frozen_plang":"","freeze_multilang_modal_title":"Select your programming language","freeze_multilang_modal_body":"Please select the programming language you want to use for this activity.","freeze_multilang_modal_note":"Note: Once confirmed, the selected programming language cannot be changed.","freeze_multilang_confirm":"Confirm","freeze_multilang_saving":"Saving...","freeze_multilang_select_error":"Please select a language.","freeze_multilang_select_label":"Language:","freeze_multilang_select_default":"-- Select language --","example":false,"comments":true,"ajaxurl":"edit.json.php?id=8852&userid=65197&action=","download":"..\/views\/downloadsubmission.php?id=8852&userid=65197","htmlconfig":0,"resetfiles":true,"maxfiles":1,"minfiles":1,"saved":true,"actualuserid":"65197","vpl_name":"WordZee","vpl_description":"<?xml encoding=\"utf-8\" ?>\n<?xml encoding=\"utf-8\" ?><?xml encoding=\"utf-8\" ?><?xml encoding=\"utf-8\" ?><?xml encoding=\"utf-8\" ?><div class=\"no-overflow\"><p><\/p><div><p paraid=\"738692707\" paraeid=\"{bcaca4e6-376a-49c9-a4c4-4d2690a21338}{161}\"><\/p><\/div><div><div><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><b>Objective:<\/b><\/span><\/p><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\">To work with strings.<\/span><\/p><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><b>Concept Explanation:<\/b><\/span><\/p><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><span><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\" style=\"\"><span data-ccp-parastyle=\"Normal (Web)\" style=\"\">The concept of strings in programming <\/span><span data-ccp-parastyle=\"Normal (Web)\" style=\"\">represents<\/span><span data-ccp-parastyle=\"Normal (Web)\" style=\"\"> sequences of characters. Strings are used to store and manipulate textual data. They can <\/span><span data-ccp-parastyle=\"Normal (Web)\" style=\"\">contain<\/span><span data-ccp-parastyle=\"Normal (Web)\" style=\"\"> letters, numbers, symbols, and whitespace. In programming languages like Java, strings are typically treated as objects, providing various methods for tasks such as concatenation, comparison, searching, and manipulation. Strings are immutable in many programming languages, meaning that once created, their values cannot be changed.<\/span><\/span><span data-ccp-props='{\"134233117\":true,\"134233118\":true,\"134245417\":true,\"134245418\":false,\"134245529\":false,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559737\":0}' style=\"\">&nbsp;<\/span><br><\/span><\/span><\/p><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><span><span data-ccp-props='{\"134233117\":true,\"134233118\":true,\"134245417\":true,\"134245418\":false,\"134245529\":false,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559737\":0}' style=\"\"><b>Concept Implementation:<\/b><\/span><\/span><\/span><\/p><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><span><span data-ccp-props='{\"134233117\":true,\"134233118\":true,\"134245417\":true,\"134245418\":false,\"134245529\":false,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559737\":0}' style=\"\"><span><div style=\"\"><p paraid=\"604918858\" paraeid=\"{a040113f-e181-4786-a397-6d9b0a203ed6}{203}\" style=\"\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\" style=\"\"><span data-ccp-parastyle=\"Normal (Web)\" style=\"\">Words and sentences are stored as strings, enabling easy manipulation and validation.&nbsp;<\/span><\/span><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><span data-ccp-parastyle=\"Normal (Web)\">Strings are checked for alphanumeric characters to ensure validity.<\/span><\/span><span data-ccp-props='{\"134233117\":true,\"134233118\":true,\"134245417\":true,\"134245418\":false,\"134245529\":false,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559737\":0}'>&nbsp;<\/span><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><span data-ccp-parastyle=\"Normal (Web)\">Words are searched within sentences using string manipulation methods.<\/span><\/span><span data-ccp-props='{\"134233117\":false,\"134233118\":false,\"134245417\":true,\"134245418\":false,\"134245529\":false,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559737\":0,\"335559738\":0,\"335559739\":0}'>&nbsp;<\/span><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><span data-ccp-parastyle=\"Normal (Web)\">Error messages are displayed if strings <\/span><span data-ccp-parastyle=\"Normal (Web)\">contain<\/span><span data-ccp-parastyle=\"Normal (Web)\"> invalid characters.<\/span><\/span><span data-ccp-props='{\"134233117\":false,\"134233118\":false,\"134245417\":true,\"134245418\":false,\"134245529\":false,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559737\":0,\"335559738\":0,\"335559739\":0}'>&nbsp;<\/span><\/p><\/div><\/span><\/span><\/span><\/span><\/p><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><b>Scenario:<\/b><\/span><\/p><p paraid=\"520659006\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{206}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\">WordZee is a famous game. It is primarily used to increase the memory of the student. The child should be able to spell the words correctly and reverse the spelling of the word, and this is how the teacher plays with the children to make them learn the spelling of the words. You, as a Java developer, help the teacher verify the children's answers in the above-mentioned context.<\/span><span data-ccp-props='{\"201341983\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"738692707\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{231}\"><b><i><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\">Constraint:<\/span><span data-ccp-props='{\"201341983\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/i><\/b><\/p><\/div><div><ol role=\"list\" start=\"1\"><li data-leveltext=\"%1.\" data-font=\"Calibri\" data-listid=\"1\" data-list-defn-props='{\"335552541\":0,\"335559684\":-1,\"335559685\":720,\"335559991\":360,\"469769242\":[65533,0],\"469777803\":\"left\",\"469777804\":\"%1.\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"1\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"554093247\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{241}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\">If there is any number or special character in the sentence then display, \"<b>&lt;sentence&gt; is an invalid sentence<\/b>\".<\/span><span data-ccp-props='{\"201341983\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/li><\/ol><\/div><div><ol role=\"list\" start=\"2\"><li data-leveltext=\"%1.\" data-font=\"Calibri\" data-listid=\"1\" data-list-defn-props='{\"335552541\":0,\"335559684\":-1,\"335559685\":720,\"335559991\":360,\"469769242\":[65533,0],\"469777803\":\"left\",\"469777804\":\"%1.\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"2\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"2007071606\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{248}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\">If there is any number or special character in the word then display, \"<b>&lt;word&gt; is an invalid word<\/b>\".<\/span><span data-ccp-props='{\"201341983\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/li><\/ol><\/div><div><ol role=\"list\" start=\"3\"><li data-leveltext=\"%1.\" data-font=\"Calibri\" data-listid=\"1\" data-list-defn-props='{\"335552541\":0,\"335559684\":-1,\"335559685\":720,\"335559991\":360,\"469769242\":[65533,0],\"469777803\":\"left\",\"469777804\":\"%1.\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"3\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"922216570\" paraeid=\"{16e3998f-5633-46db-8313-533804d0fd76}{255}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\">If the word is not in the sentence, then display, \"<b>&lt;word&gt; is not in the sentence<\/b>\".<\/span><span data-ccp-props='{\"201341983\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/li><\/ol><\/div><\/div><div><div><p paraid=\"612879845\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{11}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\"><b>Note<\/b><\/span><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">:&nbsp;<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><ul role=\"list\"><li data-leveltext=\"&iuml;&sbquo;-\" data-font=\"Symbol\" data-listid=\"2\" data-list-defn-props='{\"335552541\":1,\"335559684\":-2,\"335559685\":720,\"335559991\":360,\"469769226\":\"Symbol\",\"469769242\":[8226],\"469777803\":\"left\",\"469777804\":\"&iuml;&sbquo;-\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"1\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"2100235539\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{19}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">In the Sample Input \/ Output provided, the highlighted text in bold corresponds to the input given by the user, and the rest of the text represents the output.&nbsp;&nbsp;<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/li><li data-leveltext=\"&iuml;&sbquo;-\" data-font=\"Symbol\" data-listid=\"2\" data-list-defn-props='{\"335552541\":1,\"335559684\":-2,\"335559685\":720,\"335559991\":360,\"469769226\":\"Symbol\",\"469769242\":[8226],\"469777803\":\"left\",\"469777804\":\"&iuml;&sbquo;-\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"2\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"237430430\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{26}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Ensure to follow the object-oriented specifications provided in the question description.&nbsp;<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/li><li data-leveltext=\"&iuml;&sbquo;-\" data-font=\"Symbol\" data-listid=\"2\" data-list-defn-props='{\"335552541\":1,\"335559684\":-2,\"335559685\":720,\"335559991\":360,\"469769226\":\"Symbol\",\"469769242\":[8226],\"469777803\":\"left\",\"469777804\":\"&iuml;&sbquo;-\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"3\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"2014015936\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{33}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Ensure to provide the names for the classes, attributes, and methods as specified in the question description.&nbsp;<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/li><li data-leveltext=\"&iuml;&sbquo;-\" data-font=\"Symbol\" data-listid=\"2\" data-list-defn-props='{\"335552541\":1,\"335559684\":-2,\"335559685\":720,\"335559991\":360,\"469769226\":\"Symbol\",\"469769242\":[8226],\"469777803\":\"left\",\"469777804\":\"&iuml;&sbquo;-\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"4\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"233641756\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{40}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Adhere to the code template, if provided.<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/li><li data-leveltext=\"&iuml;&sbquo;-\" data-font=\"Symbol\" data-listid=\"2\" data-list-defn-props='{\"335552541\":1,\"335559684\":-2,\"335559685\":720,\"335559991\":360,\"469769226\":\"Symbol\",\"469769242\":[8226],\"469777803\":\"left\",\"469777804\":\"&iuml;&sbquo;-\",\"469777815\":\"hybridMultilevel\"}' aria-setsize=\"-1\" data-aria-posinset=\"4\" data-aria-level=\"1\" role=\"listitem\"><p paraid=\"233641756\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{40}\"><b>Please d<\/b><b>o not use System.exit(0) to terminate the program.<\/b><\/p><\/li><\/ul><\/div><\/div><div><p><span lang=\"EN-US\"><\/span><\/p><p><\/p><\/div><div><p paraid=\"543329457\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{51}\"><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1580694343\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{55}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Sample input and output-1<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"1016503374\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{61}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Enter a sentence<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"955011900\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{67}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">He ate a delicious pizza for dinner<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"2036075791\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{73}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Enter a word<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1323953683\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{79}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">ate<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"992867829\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{85}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">He eta a delicious pizza for dinner<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"129181299\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{91}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">&nbsp;<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1506307998\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{97}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Sample input and output-2<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"700504852\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{103}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Enter a sentence<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1373216355\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{109}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\"><b>She is studying diligently for her exams<\/b><\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"784828154\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{115}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Enter a word<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"986114030\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{121}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">e1fn<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"1459202646\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{127}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">e1fn is an invalid word<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"35860637\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{133}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">&nbsp;<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"873810411\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{139}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\"><b>Sample input and output-3<\/b><\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1072236446\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{145}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Enter a sentence<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1952613435\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{151}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">The cat chased the mouse across the room<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"153931717\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{157}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Enter a word<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"429388695\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{163}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">phoo<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"1928706932\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{169}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">phoo is not in the sentence<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"289884387\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{175}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">&nbsp;<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"39997102\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{181}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Sample input and output-4<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"1013606949\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{187}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">Enter a sentence<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1692191403\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{193}\"><b><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">I like coo9@667<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/b><\/p><\/div><div><p paraid=\"391525261\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{199}\"><span data-contrast=\"none\" xml:lang=\"EN-US\" lang=\"EN-US\">I like coo9@667 is an invalid sentence<\/span><span data-ccp-props='{\"201341983\":0,\"335551550\":1,\"335551620\":1,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><div><p paraid=\"1052547058\" paraeid=\"{5b9f29f3-6e8b-43b5-992c-4c451ace71a3}{205}\"><span data-contrast=\"auto\" xml:lang=\"EN-US\" lang=\"EN-US\"><\/span><span data-ccp-props='{\"201341983\":0,\"335559685\":0,\"335559739\":160,\"335559740\":259}'>&nbsp;<\/span><\/p><\/div><br><p><\/p><\/div>\n<?xml encoding=\"utf-8\" ?>\n","page_header":"\n            <div class=\"page-layout-header learner-header\">\n                <div class=\"header-content\">\n                    <h5 class=\"page-header-back mb-0\" data-toggle=\"tooltip\" data-placement=\"left\" title=\"Back to Core Java\">\n                        <a href=\"https:\/\/cognizant.tekstac.com\/course\/view.php?id=794&amp;cmid=8852\" class=\"prev-page-url\">\n                            <svg fill=\"black\" height=\"15px\" width=\"15px\" version=\"1.1\" id=\"page-header-back-svg\" xmlns=\"http:\/\/www.w3.org\/2000\/svg\" xmlns:xlink=\"http:\/\/www.w3.org\/1999\/xlink\" viewBox=\"0 60 511.955 511.955\" xml:space=\"preserve\">\n                                <g id=\"SVGRepo_bgCarrier\" stroke-width=\"0\"><\/g>\n                                <g id=\"SVGRepo_tracerCarrier\" stroke-linecap=\"round\" stroke-linejoin=\"round\"><\/g>\n                                <g id=\"SVGRepo_iconCarrier\">\n                                    <g>\n                                        <g>\n                                            <path d=\"M511.813,254.103c-0.96-5.227-5.653-8.853-10.88-8.853H36.293l195.2-195.093c4.053-4.267,3.947-10.987-0.213-15.04 c-4.16-3.947-10.667-3.947-14.827,0L3.12,248.45c-4.16,4.16-4.16,10.88,0,15.04l213.333,213.333 c4.267,4.053,10.987,3.947,15.04-0.213c3.947-4.16,3.947-10.667,0-14.827l-195.2-195.2h464.96 C507.76,266.583,512.88,260.717,511.813,254.103z\"><\/path>\n                                        <\/g>\n                                    <\/g>\n                                <\/g>\n                            <\/svg>\n                        <\/a>\n                        <span class=\"page-header-text ml-2\">WordZee<\/span>\n                   Back\n                        <\/h5>\n                <\/div>\n            <\/div>\n            <div class=\"page-layout-header common-header\">\n                <div class=\"header-content\">\n                    <h5 class=\"page-header-back mb-0\" data-toggle=\"tooltip\" data-placement=\"left\" title=\"Back to Core Java\">\n                        <a href=\"https:\/\/cognizant.tekstac.com\/course\/view.php?id=794&amp;cmid=8852\" class=\"prev-page-url\">\n                            <svg fill=\"black\" height=\"20px\" width=\"20px\" version=\"1.1\" id=\"page-header-back-svg\" xmlns=\"http:\/\/www.w3.org\/2000\/svg\" xmlns:xlink=\"http:\/\/www.w3.org\/1999\/xlink\" viewBox=\"0 60 511.955 511.955\" xml:space=\"preserve\">\n                                <g id=\"SVGRepo_bgCarrier\" stroke-width=\"0\"><\/g>\n                                <g id=\"SVGRepo_tracerCarrier\" stroke-linecap=\"round\" stroke-linejoin=\"round\"><\/g>\n                                <g id=\"SVGRepo_iconCarrier\">\n                                    <g>\n                                        <g>\n                                            <path d=\"M511.813,254.103c-0.96-5.227-5.653-8.853-10.88-8.853H36.293l195.2-195.093c4.053-4.267,3.947-10.987-0.213-15.04 c-4.16-3.947-10.667-3.947-14.827,0L3.12,248.45c-4.16,4.16-4.16,10.88,0,15.04l213.333,213.333 c4.267,4.053,10.987,3.947,15.04-0.213c3.947-4.16,3.947-10.667,0-14.827l-195.2-195.2h464.96 C507.76,266.583,512.88,260.717,511.813,254.103z\"><\/path>\n                                        <\/g>\n                                    <\/g>\n                                <\/g>\n                            <\/svg>\n                        <\/a>\n                       \n                  Back\n                        <\/h5>\n\n                          <span class=\"page-header-text ml-2\" data-toggle=\"tooltip\" data-placement=\"right\" title=\"WordZee\">WordZee<\/span>\n                <\/div>\n            <\/div>\n\n<script>\ndocument.addEventListener(\"DOMContentLoaded\", function () {\n\n    var headers = document.querySelectorAll(\".page-header-back\");\n    if (!headers.length) return;\n\n    headers.forEach(function (header) {\n        header.addEventListener(\"click\", function (e) {\n\n            \/\/ Allow default click if anchor itself is clicked\n            if (e.target.closest(\"a.prev-page-url\")) {\n                return;\n            }\n\n            \/\/ Find anchor inside THIS header\n            var link = header.querySelector(\"a.prev-page-url\");\n            if (link && link.href) {\n                window.location.href = link.href;\n            }\n        });\n    });\n\n});\n<\/script>","nginxconfig":null,"editortype":"default","evaltype":"0","theiaworkspace":"","maxevalrestrict":"0","aitemplate":0,"editorurl":"","showgrade":true,"showfeedback":true,"tekstacurl":"https:\/\/cognizant.tekstac.com","restrictedtheiaeditor":"1","theiainfralab":"0","alloweditor":"0","allowdesktop":"0","technologyname":"","hide_timer":false,"showseleniumbrowserlink":0,"seleniumlocalevaluation":0,"progressivemessagedelay1":4000,"progressivemessagedelay2":8000,"lastmessagedelay":5000,"completionmessagedelay":1500,"evaluationmessagedelay":1500,"browserlinkdelay":3000,"passfactor":1,"showtokens":0,"islearner":true,"maxexeprocesses":-1,"evalajaxurl":"https:\/\/cognizant.tekstac.com\/mod\/vpl\/forms\/edit.json.php","theiavplexecution":0,"isstudent":true,"theiaautosave":0,"autosave_interval":0,"dont_show_input":false,"editorview":true,"i18n":{"about":"About","acceptcertificates":"Accept self signed certificates","acceptcertificatesnote":"<p>You are using an encrypted connection.<p\/>\n<p>To use an encrypted connection with the execution servers it is required you accept its certificates.<\/p>\n<p>If you have problems with this process, you can try to use a http (unencrypted) connection or other browser.<\/p>\n<p>Please, click on the following links (server #) and accept the offered certificate.<\/p>","binaryfile":"Binary files","browserupdate":"Please update your browser to the last version<br \/>or use another that supports Websocket.","changesNotSaved":"Changes have not been saved","clipboard":"Clipboard","comments":"Result description","compilation":"Compilation","connected":"connected","connecting":"connecting","connection_closed":"connection closed","connection_fail":"connection fail","console":"Console","copy":"Copy","create_new_file":"Create a new file","cut":"Cut","debug":"Debug","debugging":"Debugging","delete":"Delete","deleteAll":"Delete All","delete_file_fq":"Are you sure you want to delete '{$a}' file?","delete_file_all":"Are you sure you want to delete all files?","delete_file_q":"Delete file?","download":"Download","edit":"Code editor","evaluate":"Evaluate","evaluate_ai":"Evaluate","evaluating":"Evaluating","execution":"Execution","getjails":"Get execution servers","file":"File","filelist":"File list","outline":"Outline","filenotadded":"File has not been added","filenotdeleted":"The '{$a}' file has NOT been deleted","filenotrenamed":"The '{$a}' file has NOT been renamed","find":"Find","find_replace":"Find\/Replace","fullscreen":"Fullscreen","incorrect_file_name":"Incorrect file name","keyboard":"Keyboard","maxfilesexceeded":"Maximum number of files exceeded","new":"New","next":"Next","load":"Load","loading":"Loading","options":"Options","outofmemory":"Out of memory","paste":"Paste","print":"Print","redo":"Redo","regularscreen":"Regular screen","rename":"Rename","rename_file":"Rename file","resetfiles":"Reset files","retrieve":"Retrieve results","run":"Run","running":"Running","save":"Save","saving":"Saving","select_all":"Select all","shortcuts":"Keyboard shortcuts","submit":"Submit","resetsubmission":"Reset submission","uploadsolution":"Upload Solution","submiting":"Submiting","sureresetfiles":"Do you want to lost all your work and reset the files to its original state?","timeleft":"Time left","timeout":"Timeout","undo":"Undo","conn_issue":"Could not connect to server. Your firewall is probably blocking the connection. Please contact your Administrator.","getS3url":"Run","getZipFileS3url":"Deploying","run_alert":"Deploying the application. Please wait for a few seconds...","execute_html":"Run","popup_alert":"Popup Alert","description":"Description","terminal_runing":"Terminal is running","terminal_runing_evaluate":"The terminal will run once done, after clicking Evaluate.","evaluate_runing":"Evaluate is running","evaluate_runing_terminal":"Evaluate is running once it is done, after clicking Run.","browser":"Open Browser","openbrowserlink":"Click <strong><em>Open Browser<\/em><\/strong> to view the browser actions","cancel":"Cancel","closebuttontitle":"Close","error":"Error","import":"Import","modified":"Modified","notice":"Notice","ok":"OK","required":"Required","sort":"Sort","warning":"Warning","close":"Close"}});
                        $JQVPL("head").append('<meta name="viewport" content="initial-scale=1">');
                        $JQVPL("head").append('<meta name="viewport" width="device-width">');
                    });
                
                          timeleft
                
                                            
                            File list
                            
                        
                        
                            
                                

<script>

$(function webAlert()
{
	//$('[name=SecondGrade]').val('');
	//$('[name=PRTypeCode]').val('');
	alert('請購金額為必要欄位，請在填單前務必詢問採購人員預估金額，以利跑後續流程');
	alert('請優先填寫 "請購類型"、"中分類"(若有中分類) ')
	//alert($('[name=PurchaseGroupCode]').val());
	
	$('[name=PRTypeCode]').change(function()
		{
			$('[name=SecondGrade]').val('');
			if($('[name=PRTypeCode]').val()=='Z010')
			{
				alert('有料號的單價：請洽資材部採購人員');
			}
			else if($('[name=PRTypeCode]').val()=='Z031')
			{
				alert('委外加工的單價：請洽資材部XXX');
			}
			else if ($('[name=PRTypeCode]').val()=='Z020' || $('[name=PRTypeCode]').val()=='Z040')
			{
				alert('中分類為必填');
			}
		});
	
	$('[name=SecondGrade]').change(function()
	{
			if($(this).val()=='4A')
			{
				alert('無料號的單價：請洽資材部XXX');
			}
			else if($(this).val()=='3A' || $(this).val()=='4B')
			{
				alert('資產類的單價：筆電類請洽IT人員');
				if($('[name=AccID]').val()=='6000' || $('[name=AccID]').val()=='0000')
				{
					alert('其他資產類相關問題，請先洽詢部門窗口，管理部 : "XXX"');
				}
				else if($('[name=AccID]').val()=='5000')
				{
					alert('其他資產類相關問題，請先洽詢部門窗口，研展部："XXX"');
				}
				else if($('[name=AccID]').val()=='4000')
				{
					alert('其他資產類相關問題，請先洽詢部門窗口，業務部："XXX"');
				}
				else if($('[name=AccID]').val()=='7000')
				{
					alert('其他資產類相關問題，請先洽詢部門窗口，品管部："XXX"');
				}
				else if($('[name=AccID]').val()=='1000')
				{
					alert('其他資產類相關問題，請先洽詢部門窗口，生產部："XXX"');
				}
				else if($('[name=AccID]').val()=='2000')
				{
					alert('其他資產類相關問題，請先洽詢部門窗口，資材部："XXX"');
				}
			}
			else if($(this).val()!='4E' && $(this).val()!='4F' && $(this).val()!=null)
			{
				if($('[name=AccID]').val()=='6000' || $('[name=AccID]').val()=='0000')
				{
					alert('資產類相關問題，請先洽詢部門窗口，管理部 : "XXX"');
				}
				else if($('[name=AccID]').val()=='5000')
				{
					alert('資產類相關問題，請先洽詢部門窗口，研展部："XXX"');
				}
				else if($('[name=AccID]').val()=='4000')
				{
					alert('資產類相關問題，請先洽詢部門窗口，業務部："XXX"');
				}
				else if($('[name=AccID]').val()=='7000')
				{
					alert('資產類相關問題，請先洽詢部門窗口，品管部："XXX"');
				}
				else if($('[name=AccID]').val()=='1000')
				{
					alert('資產類相關問題，請先洽詢部門窗口，生產部："XXX"');
				}
				else if($('[name=AccID]').val()=='2000')
				{
					alert('資產類相關問題，請先洽詢部門窗口，資材部："XXX"');
				}
			}
	});
});







var RequisitionID='(-:newtypefunc:Request("RequisitionID"):-)';
var ProcessID='(-:NewTypeFUNC:Request("ProcessID"):-)';
var ApplicantCostCenterCode; //申請人部門代碼

$().ready(function()
{
			$('[name=GuessCom]').attr('disabled',true);
			$('[name=GuessCost]').attr('disabled',true);

	var bpm = $bpm();
	
	//console.log(bpm.formInfo);
	//Send Event --------------------------------------------------
	bpm.handlerSend(function(actionInfo)//送出事件 -
	{
		//---------------------------------------------表頭檢核----------------------------------------
		if( bpm.formInfo.processID == "applicant")
		{	//送出事件為"申請"
			$("[name=DetailItem][detailtype=item] [name=CostCenterCode]").each(function(i)
			{ //成本中心"空白移除"
				var TmpStr = $(this).find(":selected").text();
				$(this).parent().find("[name=CostCenterName]").val(BlankClear(TmpStr));
			});
			
			if($('[name=PurchaseGroupCode]').val() != null)
			{//採購群組"空白移除"
				$("[name=DetailItem][detailtype=item] [name=PurchaseGroupCode]").each(function(i)
				{ 
					var TmpStr = $(this).find(":selected").text();
					$(this).parent().find("[name=PurchaseGroupName]").val(BlankClear(TmpStr));
				});
			}
			
		
			//表單送出檢核 -
			var Errmsg = "";
			var ApproverResult = $("[name=Result]").val();
			
			if($('[name=PRTypeCode]').val()=='Z020' || $('[name=PRTypeCode]').val()=='Z040')
			{//無料號、資產請購，中分類為必填
				if($('[name=SecondGrade]').val()==null)
				{
					Errmsg += "'中分類'為必填！";
				}
			}
			
			
			if( $("[name=PR_Reason]").val() == "" )
			{//請購說明必填
					Errmsg +=  "'請購說明'為必填項目！";
		   }
			
			
			if( $("[name=SecondGrade]").val() == "4E" )//若[中分類]為機構彩盒樣品製作

			{ 
				//if( $("[name=MachineName]").val() == "" )
				//	Errmsg +=  "'機種名稱'為必填項目！\n";
				//if( $("[name='RequesAccording']:checked").val() == "" )
				//	Errmsg +=  "'需求來源'為必填項目！\n";
				//if( $("[name=CustomerName]").val() == "" )
				//	Errmsg +=  "'客戶名稱'為必填項目！\n";
				//if( $("[name=SalesOfficerCode]").val() == "" )
				//	Errmsg +=  "'業務人員'為必填項目！\n";
			}
			
			if( $("[name=SecondGrade]").val() == "4F" )//若[中分類]為模具/延伸模具之製作/修改
			{ 
				if( $("[name=MachineName]").val() == "" )
					Errmsg +=  "'機種名稱'為必填項目！\n";
				if( $("[name='RequesAccording']:checked").val() == "" )
					Errmsg +=  "'需求來源'為必填項目！\n";
				//if( $("[name=CustomerName]").val() == "" )
				//	Errmsg +=  "'客戶名稱'為必填項目！\n";
				//if( $("[name=SalesOfficerCode]").val() == "" )
				//	Errmsg +=  "'業務人員'為必填項目！\n";
			}
			
			if( $("[name='RequesAccording']:checked").val() == "外部需求" )//若[需求來源]為外部需求

			{ 
				if( $("[name=CustomerName]").val() == "")
				Errmsg +=  "'客戶名稱'為必填項目！\n";
			}
			
			var test1 = $("[name=PRTypeCode]").val();
			var test2 = $("[name=PRTotalAmount]").val();
			
			
			if( $("[name=PRTypeCode]").val() == "Z040")//若為Z040，金額需為30000以上
			{
					if( $("[name=PRTotalAmount]").val() < 30000 ) Errmsg += "'請購總金額需大於3萬！";
			}
			
			if ( Errmsg != "" )
			{
				alert(Errmsg);
				return false;
			}
			
			
			var err = [];
			var msg = [];
			var budgetarray = new Map; 
		//---------------------------------------------表身檢核----------------------------------------
		
			$('[name=DetailItem][detailtype=item]').each(function(i)
			{
				
				var tmp = 0;
				
				var TmpI = i + 1;
				
				if( TmpI % 2 != 0 )
				{//列1檢核
					var PR_Materiel = $(this).find('[name=PR_Materiel]').val();
					var Short_Text = $(this).find('[name=Short_Text]').val();
					var PurchaseGroupCode = $(this).find('[name=PurchaseGroupCode]').val();
					var Quantity = $(this).find('[name=Quantity]').val();
					var D_PR_Amount = $(this).find('[name=D_PR_Amount]').val();
					var PR_D_Remark = $(this).find('[name=PR_D_Remark]').val();
					
					
					if( $("[name=PRTypeCode]").val() == "Z010" || $("[name=PRTypeCode]").val() == "Z031" )//Z010,Z031 料號必填
					{
						if( PR_Materiel == '' ) msg.push("'料號'為必填項目！");
					}
					
					if( Short_Text == '' && $("[name=SecondGrade]").val() != "4A")
					{//中分類不為4A時，短文必填
						msg.push("'短文'為必填項目！");
					}
						
					if( PurchaseGroupCode == ' '&& $("[name=SecondGrade]").val() != "4A" )
					{//中分類不為4A時，採購群組必填
						msg.push("'採購群組'為必填項目！");
					}	
					
					if( Quantity == '' ) //數量必填
					{
						msg.push("'數量'為必填項目！");
					}
					
					if( $("[name=SecondGrade]").val() == "4E" )//若[中分類]為機構彩盒樣品製作，需求備註必填

					{ 
						if( PR_D_Remark == "" )
						{
							msg.push("'需求備註說明'為必填項目！");
						}
					}
					
					if( (D_PR_Amount == '' || D_PR_Amount	<=0 )&& $("[name=SecondGrade]").val() != "4E" && $("[name=SecondGrade]").val() != "4F" )
					{
					msg.push("'請購金額'為必填項目！不能為0\n");
					}
					//if(msg.length > 0) err.push('No.'+((TmpI+1)/2)+':'+msg.join(','));
				}
				else
				{//列2檢核
					var BudgetOrderNo = $(this).find('[name=BudgetOrderNo]').val();
					var DeliverDate = $(this).find('[name=DeliverDate]').val();
					var PR_D_TotalAmount = $(this).find('[name=PR_D_TotalAmount]').val();
					var ProposeStores = $(this).find('[name=ProposeStores]').val();
					var MeasureUnit = $(this).find('[name=MeasureUnit]').val();
					var MaterielGroupName = $(this).find('[name=MaterielGroupName]').val();
					var ProjectOrderNo = $(this).find('[name=ProjectOrderNo]').val();
					
					if( $("[name=SecondGrade]").val() == "4E" || $("[name=SecondGrade]").val() == "4F" ) 
					{ //若[中分類]為機構彩盒樣品製作，廠商必填
						if( ProposeStores == "" )
							msg.push("'廠商'為必填項目！");
					}
					
					
					if($('[name=AccID]').val()=='5000')
					{//卡RD專案內部訂單必填
						if(ProjectOrderNo == "" )
						{
							msg.push("'專案內部訂單'為必填項目！");
						}
					}
					
					
					
					var BudgetAmount = ""
					
					if( $("[name=PRTypeCode]").val() == "Z040")
					{//若為Z040，預算內部訂單必填

						if( BudgetOrderNo == '' ) msg.push("'預算內部訂單'為必填項目！");
					}
					//--------------------------------------------內部預算訂單，金額控管-------------------------------
					
					
					
					
					
					if( BudgetOrderNo != "")
					{//若有填內部預算訂單           //須改改改
						$.ajax(
						{
								type: "POST",
								async:false,
								data: 
								{ 
									BudgetOrderNo : BudgetOrderNo,
									TableName : "CYP_BudgetExpenses",
									SelMode : "撈內部訂單預算",
									PR_D_TotalAmount : PR_D_TotalAmount
								},
								url: "CYP_AutoScript.aspx",
								success: function(result)
								{ //成功得到資料
									BudgetAmount = result;
								}
						});
						
						tmp = budgetarray.get(BudgetOrderNo);
						
						if( tmp == null )
						{	 
							if( (PR_D_TotalAmount > BudgetAmount)
							{
								msg.push("\n已超過內部訂單餘額！請填預算調整申請單\n頁面自動跳轉\n");
								window.location.assign("https://bpm2.cypress.com.tw/BPM/FM7_Applicant.aspx?EinB64=SWRlbnRpZnk9QnVkZ2V0UmV3cml0ZVRUJkRpc3BsYXlOYW1lPSVFOSVBMCU5MCVFNyVBRSU5NyVFOCVBQSVCRiVFNiU5NSVCNCVFNyU5NCVCMyVFOCVBQiU4QiVFNSU5NiVBRSVFNSVBRiVBNiVFNiVCOCVBQw");
							}
							else if(PR_D_TotalAmount > (BudgetAmount*0.8) && PR_D_TotalAmount<BudgetAmount)
							{
								alert('警示:"已使用預算已超過總預算80%"');
								budgetarray.set(BudgetOrderNo, (BudgetAmount-PR_D_TotalAmount));
							}
							else if((BudgetAmount*0.8) > PR_D_TotalAmount)
							{
								budgetarray.set(BudgetOrderNo, (BudgetAmount-PR_D_TotalAmount));
							}
						}
						else
						{
							if(PR_D_TotalAmount > tmp )
							{
								msg.push("\n已超過內部訂單餘額！請填預算調整申請單\n頁面自動跳轉\n");
							}
							else if(PR_D_TotalAmount > (tmp*0.8) && PR_D_TotalAmount < tmp)
							{
								alert('警示:"已使用預算已超過總預算80%"');
								budgetarray.set(BudgetOrderNo, ( tmp - PR_D_TotalAmount ));
							}
							else if((BudgetAmount*0.8) > PR_D_TotalAmount)
							{
								budgetarray.set(BudgetOrderNo, ( tmp - PR_D_TotalAmount ));
							}
						}
					}
					
					
					
					
					//4A，4B，4C，不需填物料群組 20191015嶂

					if( MaterielGroupName == "") 
					{ 
						//alert($("[name=SecondGrade]").val());
						if($("[name=SecondGrade]").val() == "4F")
						{
							msg.push("'物料群組'為必填項目！");
						}
					}
					
					if( MeasureUnit == ' '&& $("[name=SecondGrade]").val() != "4A") 
					{//中分類若為4A 計量單位為必填

						msg.push("'計量單位'為必填項目！");
					}
					
					if( DeliverDate == '' ) 
					{//交貨日期必填
						msg.push("'交貨/需求日期'為必填項目！");
					}
					
					if(msg.length > 0)
					{//檢核警示訊息
						err.push('No.'+(TmpI/2)+':'+msg.join(','));
					}
					
					msg = [];
				}
			});
			
			
			if(err.length > 0)
			{//彈出警示
				alert(err.join('\n'));
				return false;
			}
			
			TotalAmount();
			InsDTable();
			$("#PRTotalAmount").attr("disabled",false);
		}
		else if( bpm.formInfo.processID == 'SpcMem01' )
		{	//業務關卡送出檢核 -
			var Errmsg = "";
			var ApproverResult = $("[name=Result]").val();
			
			if( ApproverResult == "1" && $("[name='RequesAccording']:checked").val() == "外部需求" )
			{
				if( $("[name='PaymentType']:checked").val() == undefined ) 
				{//若[客戶付款方式]為空
					Errmsg +=  "'客戶付款方式'為必填項目！";
				}
				
				if( $("[name='PaymentType']:checked").val() == "Y" )
				{
					if( $("[name=Y_PaymentAmount]").val() == "" )
					{
						Errmsg +=  "'客戶付款金額'為必填項目！";	
					}
				}
				
				if( $("[name='PaymentType']:checked").val() == "N2" )
				{
					if( $("[name=N2_PaymentText]").val() == "" )
					{
						Errmsg +=  "'不收費說明'為必填項目！";	
					}
				}	
				
				if ( Errmsg != "" )
				{
					alert(Errmsg);
					return false;
				}
				
				var ReturnAjax = "";
				$.ajax(
				{
					type: "POST",
					async:false,
					data: 
					{ 
						RequisitionID : $("[name=RequisitionID]").val(),
						PaymentType : $("[name='PaymentType']:checked").val(),
						Y_PaymentAmount : $("[name=Y_PaymentAmount]").val(),
						N2_PaymentText : $("[name=N2_PaymentText]").val(),
						Identify : "S_MM_PRA",
						SelMode : "請購單寫入客戶付款方式"
					},
					
					url: "CYP_AutoScript.aspx",
					
					success: function(result)
					{ //成功得到資料
						ReturnAjax = result;
					}
				});		
			}
		}
		else if( bpm.formInfo.processID == 'SpcRol07' )
		{	//品保人員補充資料關卡送出檢核 -
			var ApproverResult = $("[name=Result]").val();
			
			if( ApproverResult == "1" )
			{
				var err = [];
				var msg = [];
				
				$('[name=DetailItem][detailtype=item]').each(function(i)
				{
			
					var tmp = 0;
					var TmpI = i + 1;
					
					if( TmpI % 2 != 0 )
					{
					
					}
					else
					{
						var AdjustMachineNo = $(this).find('[name=AdjustMachineNo]').val();
						
						if( AdjustMachineNo == '' ) msg.push("'校正儀器編號'為必填項目！");
		
						if(msg.length > 0) err.push('No.'+(TmpI/2)+':'+msg.join(','));
						msg = [];
					}
				});
				
				if(err.length > 0)
				{
					alert(err.join('\n'));
					return false;
				}
				InsDTable();
			}
		}
		else if( bpm.formInfo.processID == 'SpcRol08' )
		{//總務人員補充資料關卡送出檢核 -
			
			var ApproverResult = $("[name=Result]").val();
			
			if( ApproverResult == "1" )
			{
				var err = [];
				var msg = [];
				
				$('[name=DetailItem][detailtype=item]').each(function(i)
				{
			
					var tmp = 0;
					var TmpI = i + 1;
					var AUC_No;
					
					if( TmpI % 2 != 0 )
					{
						var AUC_No = $(this).find('[name=AUC_No]').val();
						
						if( AUC_No == ''  && ( $("[name=SecondGrade]").val()=="3A"||$("[name=SecondGrade]").val()=="3B"|| $("[name=SecondGrade]").val()=="3C")) msg.push("'AUC編號'為必填項目！");			
					}
					else
					{
		
						if(msg.length > 0) err.push('No.'+(TmpI/2)+':'+msg.join(','));
						msg = [];
					}
				});
				
				if(err.length > 0)
				{
					alert(err.join('\n'));
					return false;
				}
				InsDTable();
			}
		}
		
		else if( bpm.formInfo.processID == 'SpcMem13' )
		{//XXX補充資料關卡送出檢核 -
			
			var ApproverResult = $("[name=Result]").val();
			
			if( ApproverResult == "1" )
			{
				var err = [];
				var msg = [];
				
				$('[name=DetailItem][detailtype=item]').each(function(i)
				{
					var tmp = 0;
					var TmpI = i + 1;
					var AUC_No;
					
					if( TmpI % 2 != 0 )
					{
						var AUC_No = $(this).find('[name=AUC_No]').val();
						
						if( AUC_No == ''  && ( $("[name=SecondGrade]").val()=="3A"||$("[name=SecondGrade]").val()=="3B"|| $("[name=SecondGrade]").val()=="3C" || $('[name=SecondGrade]').val()=='4F')) msg.push("'AUC編號'為必填項目！");			
					}
					else
					{
						if(msg.length > 0) err.push('No.'+(TmpI/2)+':'+msg.join(','));
						msg = [];
					}
				});
				
				if(err.length > 0)
				{
					alert(err.join('\n'));
					return false;
				}
				InsDTable();
			}
		}
		
		else if( bpm.formInfo.processID == 'SpcMem12' )
		{
			//採購人員補充資料關卡送出檢核 -
			var ApproverResult = $("[name=Result]").val();
			
			if( ApproverResult == "1" )
			{
				var err = [];
				var msg = [];
				var budgetarray = new Map; 
				
				$('[name=DetailItem][detailtype=item]').each(function(i)
				{
					var tmp = 0;
					var TmpI = i + 1;
					
					if( TmpI % 2 != 0 )
					{
						var GuessCom = $(this).find('[name=GuessCom]').val();
						if( GuessCom == '' ) msg.push("'採購人員回饋廠商'為必填項目！");
					}
					else
					{
						var BudgetOrderNo = $(this).find('[name=BudgetOrderNo]').val();
						var GuessCost = $(this).find('[name=GuessCost]').val();
						if( GuessCost == '' ) msg.push("'採購人員回饋金額'為必填項目！");
						
						var BudgetAmount = ""
						
				      if(BudgetOrderNo!="")
						{
							$.ajax(
							{
										type: "POST",
										async:false,
										data: 
										{ 
												BudgetOrderNo : BudgetOrderNo,
												TableName : "CYP_BudgetExpenses",
												SelMode : "撈內部訂單預算",
												PR_D_TotalAmount : PR_D_TotalAmount
										},
										url: "CYP_AutoScript.aspx",
									
									success: function(result)
									{ //成功得到資料
									BudgetAmount = result;
									}
							});
							
							tmp = budgetarray.get(BudgetOrderNo);
							
							if( tmp == null )
							{	 
								if( (BudgetAmount - PR_D_TotalAmount ) < 0 )
								{
									msg.push("已超過內部訂單餘額！")
								}
								budgetarray.set(BudgetOrderNo, (BudgetAmount-PR_D_TotalAmount));
							}
							else
							{
								if( ( tmp - PR_D_TotalAmount ) >= 0 )
								{
									budgetarray.set(BudgetOrderNo, ( tmp - PR_D_TotalAmount ));
								}
								else
								{
									msg.push("已超過內部訂單餘額！")
								}
							}
						}
						
						if(msg.length > 0) 
						{
							err.push('No.'+(TmpI/2)+':'+msg.join(','));
						}
						msg = [];
					}
				});
				
				if(err.length > 0)
				{
					alert(err.join('\n'));
					return false;
				}
				
				TotalAmount();
				
				var ReturnAjax = "";
				
				$.ajax(
				{
					type: "POST",
					async:false,
					
					data: 
					{ 
						PRTotalAmount : $("[name=PRTotalAmount]").val(),
						RequisitionID : $("[name=RequisitionID]").val(),
						Identify : "S_MM_PRA",
						SelMode : "請購單更新總金額"
					},
					
					url: "CYP_AutoScript.aspx",
					
					success: function(result)
					{ //成功得到資料
						ReturnAjax = result;
					}
				});		
				
				InsDTable();
			}
		}
		return true;
	});
	
	//Object Event --------------------------------------------------
	bpm.detail.handlerAddItemEnd(function(detailId, detailItem)
	{	

		loadDetailNo();
	});
	
	$("#ApplicantName").mousedown(function()
	{	//選擇申請人

		AccChoose('0', 'Applicant', 'ApplicantID', 'ApplicantName', 'ApplicantDept', 'ApplicantDeptName', 'FM7_AccountChoose_OrgTree1');
	});
	
	$("#SalesOfficerName").mousedown(function()
	{	//業務人員
		AccChoose('0', 'Applicant', 'SalesOfficerCode', 'SalesOfficerName', '', '', 'FM7_AccountChoose_OrgTree0');
	});
	
	$("[name=PRTypeCode]").change(function()
	{	//類型"網頁功能"
	
		var PRTypeCode = $("[name=PRTypeCode]").val();
		var CheckS = "";
		
		$.ajax(
		{
			type: "POST",
			async:false,
			
			data: 
			{ 
				PK : PRTypeCode,
				TableName : "CYP_PRType",
				SelMode : "查詢資料"
			},
			
			url: "CYP_AutoScript.aspx",
			
			success: function(result)
			{ //成功得到資料
				CheckS = result;
			}
		});
		
		$("[name=ACCTASSCAT]").val(CheckS);
		$("[name=SecondGrade]").change();
		
		
		$('#DetailTable tbody [name=tdSid]').each(function()
		{
			bpm.detail.delItem(this);
		});
		
		if ($('#DetailTable tbody tr').length == 2 )
		{
			bpm.detail.addItem('Detail');
		}
		
		$("[name=CostCenterCode]").each(function(i)
		{
			$(this).val(ApplicantCostCenterCode);
		});
		
		if( PRTypeCode == "Z010" || PRTypeCode == "Z031")
		{ //採購類型 = 一般請購單 或 委外加工請購單

			$("[name=PR_Materiel]").each(function()
			{
				$(this).attr("readonly","readonly");
			});
			
			//$("#RequesAccording").val("");
			$("[name=RequesAccording]").attr("disabled","disabled");
			$("#RequesAccordingTD").attr("style","background-color:#EBEBE4");			
			//$("#MachineName").val("");				
			$("#MachineName").attr("disabled","disabled");
			$("#MachineNameTD").attr("style","background-color:#EBEBE4");
			//$("#CustomerName").val("");
			$("#CustomerName").attr("disabled","disabled");
			$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
			//$("#SalesOfficerName").val("");			
			$("#SalesOfficerName").attr("disabled","disabled");
			$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");	
			
			//$("[name=PR_Materiel]").val("");
			$("[name=PR_Materiel]").attr("disabled",false);//能填料號
			$("[name=PR_MaterielBtn]").attr("disabled",false);
			$("[name=PR_MaterielTD]").attr("style","background-color:#FFFFFF");
			//$("[name=MaterielGroupName]").val("");
			$("[name=MaterielGroupName]").attr("disabled",false);//能填物料群組
			$("[name=MaterielGroupBtn]").attr("disabled",false);
			$("[name=MaterielGroupNameTD]").attr("style","background-color:#FFFFFF");
			//$("[name=Short_Text]").val("");
			$("[name=Short_Text]").attr("disabled",false);	//能填短文
			$("[name=Short_TextTD]").attr("style","background-color:#FFFFFF");
			//$("[name=BudgetOrderNo]").val("");
			$("[name=BudgetOrderNo]").attr("disabled","disabled");//不能填預算內部訂單		
			$("[name=BudgetOrderNoTD]").attr("style","background-color:#EBEBE4");
			//$("[name=PurchaseGroupCode]").val("");//採購群組不預設	
		}
		
		
		
		else if(PRTypeCode == "Z040")
		{									//採購類型 = 資產請購(NT3萬以上)
			$("[name=PR_Materiel]").each(function(){
				$(this).removeAttr("readonly");
			});
			//$("#RequesAccording").val("");
			$("[name=RequesAccording]").attr("disabled","disabled");
			$("#RequesAccordingTD").attr("style","background-color:#EBEBE4");			
			//$("#MachineName").val("");				
			$("#MachineName").attr("disabled","disabled");
			$("#MachineNameTD").attr("style","background-color:#EBEBE4");
			//$("#CustomerName").val("");
			$("#CustomerName").attr("disabled","disabled");
			$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
			//$("#SalesOfficerName").val("");			
			$("#SalesOfficerName").attr("disabled","disabled");
			$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");	
				
			//$("[name=PR_Materiel]").val("");
			$("[name=PR_Materiel]").attr("disabled","disabled");//不能填料號 
			$("[name=PR_MaterielBtn]").attr("disabled","disabled");
			$("[name=PR_MaterielTD]").attr("style","background-color:#EBEBE4");
			//$("[name=MaterielGroupName]").val("");
			$("[name=MaterielGroupName]").attr("disabled",false);//能填物料群組
			$("[name=MaterielGroupBtn]").attr("disabled",false);
			$("[name=MaterielGroupNameTD]").attr("style","background-color:#FFFFFF");
			//$("[name=Short_Text]").val("");
			$("[name=Short_Text]").attr("disabled",false);//能填短文	
			$("[name=Short_TextTD]").attr("style","background-color:#FFFFFF");
			//$("[name=BudgetOrderNo]").val("");
			$("[name=BudgetOrderNo]").attr("disabled",false);//能填預算內部訂單		
			$("[name=BudgetOrderNoTD]").attr("style","background-color:#FFFFFF");
			//$("[name=PurchaseGroupCode]").val("");//採購群組不預設	

		}
		else
		{																		//採購類型 = 費用類跨單位
			$("[name=PR_Materiel]").each(function(){
				$(this).removeAttr("readonly");
			});	
			//$("#RequesAccording").val("");
			$("[name=RequesAccording]").attr("disabled","disabled");
			$("#RequesAccordingTD").attr("style","background-color:#EBEBE4");			
			//$("#MachineName").val("");				
			$("#MachineName").attr("disabled","disabled");
			$("#MachineNameTD").attr("style","background-color:#EBEBE4");
			//$("#CustomerName").val("");
			$("#CustomerName").attr("disabled","disabled");
			$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
			//$("#SalesOfficerName").val("");			
			$("#SalesOfficerName").attr("disabled","disabled");
			$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");	
			
			//$("[name=PR_Materiel]").val("");
			$("[name=PR_Materiel]").attr("disabled",false);//能填料號 
			$("[name=PR_MaterielBtn]").attr("disabled",false);
			$("[name=PR_MaterielTD]").attr("style","background-color:#FFFFFF");
			//$("[name=MaterielGroupName]").val("");
			$("[name=MaterielGroupName]").attr("disabled",false);//能填物料群組
			$("[name=MaterielGroupBtn]").attr("disabled",false);
			$("[name=MaterielGroupNameTD]").attr("style","background-color:#FFFFFF");
			//$("[name=Short_Text]").val("");
			$("[name=Short_Text]").attr("disabled",false);//能填短文	
			$("[name=Short_TextTD]").attr("style","background-color:#FFFFFF");
			//$("[name=BudgetOrderNo]").val("");
			$("[name=BudgetOrderNo]").attr("disabled","disabled");//不能填預算內部訂單		
			$("[name=BudgetOrderNoTD]").attr("style","background-color:#EBEBE4");
			//$("[name=PurchaseGroupCode]").val("");//採購群組不預設	
			
			var SecondGrade = $("[name=SecondGrade]").val();
			if( SecondGrade == "4A"){													//無料號

				//$("[name=PR_Materiel]").val("");
				$("[name=PR_Materiel]").attr("disabled","disabled");//不能填料號 
				$("[name=PR_MaterielBtn]").attr("disabled","disabled");
				$("[name=PR_MaterielTD]").attr("style","background-color:#EBEBE4");
				//$("[name=MaterielGroupName]").val("");
				$("[name=MaterielGroupName]").attr("disabled","disabled");//不能填物料群組


				$("[name=MaterielGroupBtn]").attr("disabled","disabled");
				$("[name=MaterielGroupNameTD]").attr("style","background-color:#EBEBE4");
				//$("[name=Short_Text]").val("");
				$("[name=Short_Text]").attr("disabled","disabled");//不能填短文	
				$("[name=Short_TextTD]").attr("style","background-color:#EBEBE4");
				//$("[name=BudgetOrderNo]").val("");
				$("[name=BudgetOrderNo]").attr("disabled","disabled");//不能填預算內部訂單		
				$("[name=BudgetOrderNoTD]").attr("style","background-color:#EBEBE4");
				$("[name=PurchaseGroupCode]").val("TP6");//採購群組預設XXX


			}
		}
	});
	
	$("[name=SecondGrade]").change(function()
	{				//若改變中分類"網頁功能"
		var SecondGrade = $("[name=SecondGrade]").val();
		if(SecondGrade == "3A"||SecondGrade == "3B"||SecondGrade == "3C"){
		//$("#RequesAccording").val("");
			$("[name=RequesAccording]").attr("disabled","disabled");
			$("#RequesAccordingTD").attr("style","background-color:#EBEBE4");			
			//$("#MachineName").val("");				
			$("#MachineName").attr("disabled","disabled");
			$("#MachineNameTD").attr("style","background-color:#EBEBE4");
			//$("#CustomerName").val("");
			$("#CustomerName").attr("disabled","disabled");
			$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
			//$("#SalesOfficerName").val("");			
			$("#SalesOfficerName").attr("disabled","disabled");
			$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");	
				
			//$("[name=PR_Materiel]").val("");
			$("[name=PR_Materiel]").attr("disabled","disabled");//不能填料號 
			$("[name=PR_MaterielBtn]").attr("disabled","disabled");
			$("[name=PR_MaterielTD]").attr("style","background-color:#EBEBE4");
			//$("[name=MaterielGroupName]").val("");
			$("[name=MaterielGroupName]").attr("disabled",false);//能填物料群組
			$("[name=MaterielGroupBtn]").attr("disabled",false);
			$("[name=MaterielGroupNameTD]").attr("style","background-color:#FFFFFF");
			//$("[name=Short_Text]").val("");
			$("[name=Short_Text]").attr("disabled",false);//能填短文	
			$("[name=Short_TextTD]").attr("style","background-color:#FFFFFF");
			//$("[name=BudgetOrderNo]").val("");
			$("[name=BudgetOrderNo]").attr("disabled",false);//能填預算內部訂單		
			$("[name=BudgetOrderNoTD]").attr("style","background-color:#FFFFFF");
			$("[name=PurchaseGroupCode]").val("總務-王柏鈞");//採購群組不預設	
		}
		
		else if( SecondGrade == "4A")									//無料號

		{																		
				//$("#RequesAccording").val("");
				$("[name=RequesAccording]").attr("disabled","disabled");
				$("#RequesAccordingTD").attr("style","background-color:#EBEBE4");			
				//$("#MachineName").val("");				
				$("#MachineName").attr("disabled","disabled");
				$("#MachineNameTD").attr("style","background-color:#EBEBE4");
				//$("#CustomerName").val("");
				$("#CustomerName").attr("disabled","disabled");
				$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
				//$("#SalesOfficerName").val("");			
				$("#SalesOfficerName").attr("disabled","disabled");
				$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");	
				
				//$("[name=PR_Materiel]").val("");
				$("[name=PR_Materiel]").attr("disabled","disabled");//不能填料號 
				$("[name=PR_MaterielBtn]").attr("disabled","disabled");
				$("[name=PR_MaterielTD]").attr("style","background-color:#EBEBE4");
				//$("[name=MaterielGroupName]").val("");
				$("[name=MaterielGroupName]").attr("disabled","disabled");//不能填物料群組

				$("[name=MaterielGroupBtn]").attr("disabled","disabled");
				$("[name=MaterielGroupNameTD]").attr("style","background-color:#EBEBE4");
				//$("[name=Short_Text]").val("");
				$("[name=Short_Text]").attr("disabled","disabled");//不能填短文	
				$("[name=Short_TextTD]").attr("style","background-color:#EBEBE4");
				//$("[name=BudgetOrderNo]").val("");
				$("[name=BudgetOrderNo]").attr("disabled","disabled");//不能填預算內部訂單		
				$("[name=BudgetOrderNoTD]").attr("style","background-color:#EBEBE4");
				$("[name=PurchaseGroupCode]").val("TP6");//採購群組預設王繼忠

		}
		
		else if(SecondGrade == "4B"||SecondGrade == "4C"||SecondGrade == "4D")//固定資產(3萬以下)
		{			
				//$("#RequesAccording").val("");
				$("[name=RequesAccording]").attr("disabled","disabled");
				$("#RequesAccordingTD").attr("style","background-color:#EBEBE4");			
				//$("#MachineName").val("");				
				$("#MachineName").attr("disabled","disabled");
				$("#MachineNameTD").attr("style","background-color:#EBEBE4");
				//$("#CustomerName").val("");
				$("#CustomerName").attr("disabled","disabled");
				$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
				//$("#SalesOfficerName").val("");			
				$("#SalesOfficerName").attr("disabled","disabled");
				$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");	
				
				
				$("[name=PR_Materiel]").val("");
				$("[name=PR_Materiel]").attr("disabled","disabled");//不能填料號 
				$("[name=PR_MaterielBtn]").attr("disabled","disabled");
				$("[name=PR_MaterielTD]").attr("style","background-color:#EBEBE4");
				//$("[name=MaterielGroupName]").val("");
				$("[name=MaterielGroupName]").attr("disabled",'disabled');//不能填物料群組20191015嶂

				$("[name=MaterielGroupNameTD]").attr("style","background-color:#EBEBE4");//不能填物料群組20191015嶂

				$("[name=MaterielGroupBtn]").attr("disabled",'disabled');
				//$("[name=MaterielGroupNameTD]").attr("style","background-color:#FFFFFF");
				//$("[name=Short_Text]").val("");
				$("[name=Short_Text]").attr("disabled",false);//能填短文	
				$("[name=Short_TextTD]").attr("style","background-color:#FFFFFF");
				$("[name=BudgetOrderNo]").val("");
				$("[name=BudgetOrderNo]").attr("disabled","disabled");//不能填預算內部訂單		
				$("[name=BudgetOrderNoTD]").attr("style","background-color:#EBEBE4");
				//$("[name=PurchaseGroupCode]").val("");//採購群組不預設

		}
		
		else if(SecondGrade == "4E")												//機構彩盒
		{																	
				//$("#RequesAccording").val("");
				$("[name=RequesAccording]").attr("disabled","disabled");
				$("#RequesAccordingTD").attr("style","background-color:#EBEBE4");			
				//$("#MachineName").val("");				
				$("#MachineName").attr("disabled","disabled");
				$("#MachineNameTD").attr("style","background-color:#EBEBE4");
				//$("#CustomerName").val("");
				$("#CustomerName").attr("disabled","disabled");
				$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
				//$("#SalesOfficerName").val("");			
				$("#SalesOfficerName").attr("disabled","disabled");
				$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");			
							
				//$("[name=PR_Materiel]").val("");
				$("[name=PR_Materiel]").attr("disabled",false);//能填料號 
				$("[name=PR_MaterielBtn]").attr("disabled",false);
				$("[name=PR_MaterielTD]").attr("style","background-color:#FFFFFF");
				//$("[name=MaterielGroupName]").val("");
				$("[name=MaterielGroupName]").attr("disabled",false);//能填物料群組
				$("[name=MaterielGroupBtn]").attr("disabled",false);
				$("[name=MaterielGroupNameTD]").attr("style","background-color:#FFFFFF");
				//$("[name=Short_Text]").val("");
				$("[name=Short_Text]").attr("disabled",false);//能填短文	
				$("[name=Short_TextTD]").attr("style","background-color:#FFFFFF");
				//$("[name=BudgetOrderNo]").val("");
				$("[name=BudgetOrderNo]").attr("disabled","disabled");//不能填預算內部訂單		
				$("[name=BudgetOrderNoTD]").attr("style","background-color:#EBEBE4");
				//$("[name=PurchaseGroupCode]").val("");//採購群組不預設

		}
		
		else																			//模具
		{																									
				//$("#RequesAccording").val("");
				$("[name=RequesAccording]").attr("disabled",false);
				$("#RequesAccordingTD").attr("style","background-color:#FFFFFF");			
				//$("#MachineName").val("");				
				$("#MachineName").attr("disabled",false);
				$("#MachineNameTD").attr("style","background-color:#FFFFFF");
				//$("#CustomerName").val("");
				$("#CustomerName").attr("disabled","disabled");
				$("#CustomerNameTD").attr("style","background-color:#EBEBE4");
				//$("#SalesOfficerName").val("");			
				$("#SalesOfficerName").attr("disabled","disabled");
				$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");	
				
				//$("[name=PR_Materiel]").val("");
				$("[name=PR_Materiel]").attr("disabled",false);//能填料號 
				$("[name=PR_MaterielBtn]").attr("disabled",false);
				$("[name=PR_MaterielTD]").attr("style","background-color:#FFFFFF");
				//$("[name=MaterielGroupName]").val("");
				$("[name=MaterielGroupName]").attr("disabled",false);//能填物料群組
				$("[name=MaterielGroupBtn]").attr("disabled",false);
				$("[name=MaterielGroupNameTD]").attr("style","background-color:#FFFFFF");
				//$("[name=Short_Text]").val("");
				$("[name=Short_Text]").attr("disabled",false);//能填短文	
				$("[name=Short_TextTD]").attr("style","background-color:#FFFFFF");
				//$("[name=BudgetOrderNo]").val("");
				$("[name=BudgetOrderNo]").attr("disabled","disabled");//不能填預算內部訂單		
				$("[name=BudgetOrderNoTD]").attr("style","background-color:#EBEBE4");
				//$("[name=PurchaseGroupCode]").val("");//採購群組不預設		
		}
	});
	
	$("[name=PR_Currency]").change(function()
	{//改變幣別 網頁功能
		var PR_Currency = $("[name=PR_Currency]").val();
		
		if( PR_Currency == "TWD" )
		{
			$("[name=PR_Rate]").val("1");
			$("[name=PR_Rate]").attr("readonly","readonly");
		}
		else
		{
			$("[name=PR_Rate]").val("");
			$("[name=PR_Rate]").removeAttr("readonly");
		}
	});
	
	$("[name=PR_Rate]").change(function()
	{//匯率，網頁功能

		reg = /[1-9]\d*\.?\d{1,2}|[0]\.\d{1,2}|\d/;
		$("[name=PR_Rate]").val(reg.exec($(this).val()));
		TotalAmount();
	});
	
	//業務欄位
	
	$("[name=RequesAccording]").change(function()
	{//需求來源改變，網頁功能
		if( $("[name='RequesAccording']:checked").val() == "外部需求" )
		{
			$("#CustomerNameTD").attr("style","background-color:#FFFFFF");
			$("#CustomerName").attr("disabled",false);
			$("#SalesOfficerCodeTD").attr("style","background-color:#FFFFFF");		
			$("#SalesOfficerName").attr("disabled",false);
		}
		else
		{
			$("#CustomerNameTD").attr("style","background-color:#EBEBE4");//停用客戶名稱
			$("#CustomerName").attr("disabled","disabled");
			$("#CustomerName").val("");
			$("#SalesOfficerCodeTD").attr("style","background-color:#EBEBE4");//停用業務人員
			$("#SalesOfficerName").attr("disabled","disabled");
		}
	});	
	
	/*$("[name=SalesOfficerName]").change(function(){
		var SalesOfficerName= $("[name=SalesOfficerName]").val();		
		//ar ApplicantName = Request("ApplicantName");
		var SQLStr = "select AccountID from FSe7en_Org_MemberInfo where DisplayName = '"+SalesOfficerName+"' ";
		//SELECT AccountID FROM [dbo].[FSe7en_Org_MemberInfo] WHERE DisplayName='王繼忠'
		var result = ExecSqlQuery(SQLStr);
		$("[name=SalesOfficerCode]").val(result);
		//write(result);
		//GetFieldValue("SalesOfficerCode")
	});*/
	
	$("[name=PaymentType]").change(function()
	{//客戶付款方式改變  網頁功能
		var TmpVal = $("[name='PaymentType']:checked").val();
		
		if( TmpVal == "Y" )
		{
			$("#Y_PaymentAmount").removeAttr("disabled");
			$("#N2_PaymentText").attr("disabled","disabled");
			$("#N2_PaymentText").val("");
		}
		else if( TmpVal == "N1" )
		{
			$("#Y_PaymentAmount").attr("disabled","disabled");
			$("#N2_PaymentText").attr("disabled","disabled");
			$("#N2_PaymentText").val("");
			$("#Y_PaymentAmount").val("");
		}
		else if( TmpVal == "N2" )
		{
			$("#Y_PaymentAmount").attr("disabled","disabled");
			$("#Y_PaymentAmount").val("");
			$("#N2_PaymentText").removeAttr("disabled");
		}
	});
	
	//D表加減欄位

	
	$('[name=imgAddDetail]').click(function()
	{//增加一列表格==
		bpm.detail.addItem('Detail');
		
		$("[name=CostCenterCode]").each(function(i)
		{
			$(this).val(ApplicantCostCenterCode);
		});
	});
	
	
	$('[name=imgDelDetail]').click(function()
	{//刪除該列表格==
		$('#DetailTable tbody [name^=cbID]:checked').each(function()
		{//刪除該列表格==
			bpm.detail.delItem(this);
			
			//最少保留一列==
			if ($('#DetailTable tbody tr').length == 2 )
			{//增加一列表格==
				bpm.detail.addItem('Detail');
			}
		});
		TotalAmount();
	});
	
	$("#DetailTable").delegate("[name=PR_MaterielBtn]","click",function()
	{//選擇料號 "按鈕"
		var detailitemid = $(this).parents('tr:first').attr("detailitemid");
		var Element = this;
		
		var Dialog = newDialog(
		{
			height: 520,
			width: 1150,
			title : '請選擇物料',
			src: 'CYP_GetMateriel.aspx',
			
			load: function(frameDialog)
			{
				//item 點擊事件-
				$(frameDialog.content).find('#divSelector').delegate('a[name=dataItem]','click',function(){
					var tr = $(Element).parents('tbody:first');
					var data = JSON.parse($(this).attr('dataitem'));

					$(tr).find("[detailitemid='"+detailitemid+"'] [name=PR_Materiel]").val(data['MATNR']);			//物料
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=Short_Text]").val(data['MAKTX']);			//短文
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=MaterielGroupCode]").val(data['MATKL']);	//物料群組碼







					$(tr).find("[detailitemid='"+detailitemid+"'] [name=PurchaseGroupCode]").val(data['EKGRP']);	//採購群組
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=MeasureUnit]").val(data['MEINS']);			//計量單位
					
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=PR_Materiel]").attr("readonly","readonly");		
					//$(tr).find("[detailitemid='"+detailitemid+"'] [name=MaterielGroupCode]").attr("disabled","disabled");
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=MaterielGroupCode]").attr("readonly","readonly");		
					//$(tr).find("[detailitemid='"+detailitemid+"'] [name=MeasureUnit]").attr("disabled","disabled");
					
					var ReturnAjax = "";
					$.ajax({
						type: "POST",
						async:false,
						data: { 
							MaterielGroupCode : data['MATKL'],
							SelMode : "撈物料群組值"
						},
						url: "CYP_AutoScript.aspx",
						success: function(result){ //成功得到資料
							ReturnAjax = result;
						}
					});		
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=MaterielGroupName]").val(ReturnAjax);	//物料群組值







					
					frameDialog.close();
				});
			},
			buttons: 
			[
				//{
				//	text: 'MISC',
				//	func: function(objDialog){
				//		$("[name=apa05]").val("MISC");
				//		$("[name=MFRName]").val("MISC");
				//		$("[name=MFRName]").removeAttr('readonly');
				//		objDialog.close();
				//	}
				//},
				{
					text: '取消',
					func: function(objDialog){
						objDialog.close();
					}
				}
			]
		});
		Dialog.open();
	});
	
	$("#DetailTable").delegate("[name=MaterielGroupBtn]","click",function(){
		var detailitemid = $(this).parents('tr:first').attr("detailitemid");
		var Element = this;
		var Dialog = newDialog({
			height: 520,
			width: 1150,
			title : '請選擇物料群組',
			src: 'CYP_GetMaterielGroupCode.aspx',
			load: function(frameDialog){
				//item 點擊事件-
				$(frameDialog.content).find('#divSelector').delegate('a[name=dataItem]','click',function(){
					var tr = $(Element).parents('tbody:first');
					var data = JSON.parse($(this).attr('dataitem'));

					$(tr).find("[detailitemid='"+detailitemid+"'] [name=MaterielGroupCode]").val(data['MaterielGroupCode']);			
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=MaterielGroupName]").val(data['MaterielGroupName']);
					frameDialog.close();
				});
			},
			buttons: 
			[
				{
					text: '取消',
					func: function(objDialog){
						objDialog.close();
					}
				}
			]
		});
		Dialog.open();
	});
	
	$("#DetailTable").delegate("[name=ProjectOrderNo]","click",function(){
		var detailitemid = $(this).parents('tr:first').attr("detailitemid");
		var Element = this;
		//var tr = $(Element).parents('tbody:first');
		
		var Dialog = newDialog({
			height: 400,
			width: 1000,
			title : '請選擇專案內部訂單',
			src: 'CYP_ProjectOrderNo.aspx',
			load: function(frameDialog){
				//item 點擊事件-
				$(frameDialog.content).find('#divSelector').delegate('a[name=dataItem]','click',function(){
					var tr = $(Element).parents('tbody:first');
					var data = JSON.parse($(this).attr('dataitem'));
					$(tr).find("[detailitemid='"+detailitemid+"'] [name=ProjectOrderNo]").val(data['ProjectOrderNo']);
					frameDialog.close();
				});
			},
			buttons: 
			[
				{
					text: '取消',
					func: function(objDialog){
						objDialog.close();
					}
				}
			]
		});
		Dialog.open();
	});
	
	$("#DetailTable").delegate("[name=D_PR_Amount]","change",function(){
		reg = /[1-9]\d*\.?\d{1,2}|[0]\.\d{1,2}|\d/;
		var TmpVal = reg.exec($(this).val());
		$(this).val(TmpVal);
		
		TotalAmount();
		//var TotalAmount = 0;
		//$("[name=D_PR_Amount]").each(function(i){
		//	if( $(this).val() != "" ){
		//		if( $(this).closest('tr').find('[name=Quantity]').val() != "" ){
		//			var TmpAMT = FloatMul(reg.exec($(this).val()),$(this).closest('tr').find('[name=Quantity]').val());			
		//			TotalAmount = FloatAdd(TotalAmount,TmpAMT);
		//		}
		//	}
		//});	
		//$("[name=PRTotalAmount]").val(FloatMul(TotalAmount,$("[name=PR_Rate]").val()));
		if( $(this).closest('tr').find('[name=Quantity]').val() != "" ){
			var detailitemid = $(this).parents('tr:first').attr("detailitemid");
			$(this).parents('tbody:first').find("[detailitemid='"+detailitemid+"'] [name=PR_D_TotalAmount]").val(FloatMul($(this).val(),$(this).closest('tr').find('[name=Quantity]').val()));
		}
		
	});
	
	$("#DetailTable").delegate("[name=Quantity]","keyup",function(){

		TotalAmount();
		//var TotalAmount = 0;
		//$("[name=Quantity]").each(function(i){
		//	if( $(this).val() != "" ){
		//		//if( $(this).closest('tr').find('[name=D_PR_Amount]').val() == "" )
		//		//	$(this).closest('tr').find('[name=D_PR_Amount]').val("1");
		//		if( $(this).closest('tr').find('[name=D_PR_Amount]').val() != "" ){
		//			var TmpAMT = FloatMul($(this).val(),$(this).closest('tr').find('[name=D_PR_Amount]').val());			
		//			TotalAmount = FloatAdd(TotalAmount,TmpAMT);
		//		}
		//	}
		//});	
		//$("[name=PRTotalAmount]").val(FloatMul(TotalAmount,$("[name=PR_Rate]").val()));
		if( $(this).closest('tr').find('[name=D_PR_Amount]').val() != "" ){
			var detailitemid = $(this).parents('tr:first').attr("detailitemid");
			$(this).parents('tbody:first').find("[detailitemid='"+detailitemid+"'] [name=PR_D_TotalAmount]").val(FloatMul($(this).val(),$(this).closest('tr').find('[name=D_PR_Amount]').val()));
		}
	});
	
	$("#DetailTable").delegate("[name=BudgetOrderNo]","click",function(){
		var detailitemid = $(this).parents('tr:first').attr("detailitemid");
		var Element = this;
		var tr = $(Element).parents('tbody:first');
		
		var Dialog = newDialog({
			height: 400,
			width: 1000,
			title : '請選擇預算內部訂單',
			src: 'CYP_GetCostCenterBudgetMapping.aspx?CostCenterCode='+$(tr).find("[detailitemid='"+detailitemid+"'] [name=CostCenterCode]").val(),
			load: function(frameDialog){
				//item 點擊事件-
				$(frameDialog.content).find('#divSelector').delegate('a[name=dataItem]','click',function(){
					var data = JSON.parse($(this).attr('dataitem'));

					$(tr).find("[detailitemid='"+detailitemid+"'] [name=BudgetOrderNo]").val(data['BudgetOrderNo']);			
					frameDialog.close();
				});
			},
			buttons: 
			[
				{
					text: '取消',
					func: function(objDialog){
						objDialog.close();
					}
				}
			]
		});
		Dialog.open();
	});
	
	$("#DetailTable").delegate("[name=DeliverDate]","focus",function(){
		WdatePicker({dateFmt:'yyyyMMdd',minDate:'%y-%M-%d'});
	});
	
	//View Setting --------------------------------------------------
	//定義 Detail -
	bpm.detail.setTemplate({detailId:'Detail', target: '[name=DetailItem]'});
	
	//表單載入事件 -
	var loadDetailItem = function(detailData){
		$(detailData).each(function(i, o){
			var item = bpm.detail.addItem('Detail');
			
			$(item).find('[name=tdSid]').val(o.tdSid);
			$(item).find('[name=PR_Materiel]').val(o.PR_Materiel);
			$(item).find('[name=Short_Text]').val(o.Short_Text);
			$(item).find('[name=PurchaseGroupName]').val(o.PurchaseGroupName);
			$(item).find('[name=PurchaseGroupCode]').val(o.PurchaseGroupCode);
			$(item).find('[name=Quantity]').val(o.Quantity);
			$(item).find('[name=D_PR_Amount]').val(o.D_PR_Amount);
			$(item).find('[name=CostCenterName]').val(o.CostCenterName);
			$(item).find('[name=CostCenterCode]').val(o.CostCenterCode);
			$(item).find('[name=DeliverDate]').val(o.DeliverDate);
			$(item).find('[name=AUC_No]').val(o.AUC_No);
			$(item).find('[name=MaterielGroupName]').val(o.MaterielGroupName);
			$(item).find('[name=MaterielGroupCode]').val(o.MaterielGroupCode);
			$(item).find('[name=ProposeStores]').val(o.ProposeStores);
			$(item).find('[name=ProjectOrderNo]').val(o.ProjectOrderNo);
			$(item).find('[name=MeasureUnit]').val(o.MeasureUnit);
			$(item).find('[name=PR_D_TotalAmount]').val(o.PR_D_TotalAmount);
			$(item).find('[name=BudgetOrderNo]').val(o.BudgetOrderNo);
			$(item).find('[name=PR_D_Remark]').val(o.PR_D_Remark);
			$(item).find('[name=AdjustMachineNo]').val(o.AdjustMachineNo);
			$(item).find('[name=GuessCom]').val(o.GuessCom);
			$(item).find('[name=GuessCost]').val(o.GuessCost);
			loadDetailNo();
		});
	}
	var detailData = GetBPMDetail({Identify:'S_MM_PRA', RequisitionID:bpm.formInfo.requisitionID});
	loadDetailItem(detailData);
	
	//process ----------------------------------------------------
	
	$("[name^=CostCenterName]").hide();
	$("[name^=PurchaseGroupName]").hide();
	$("[name^=MaterielGroupCode]").hide();
	
	if( $("[name=PaymentType]").val() != "" )
		$("[name='PaymentType'][value='"+$("[name=PaymentType]").val()+"']").prop("checked",true);
	
	
	if( bpm.formInfo.processID == 'applicant' ){	
		var Refill='(-:newtypefunc:Request("refill"):-)';
	
		//一般填單




		if( ProcessID == "" && RequisitionID == "" ){
		
			$("[name=PRTypeCode]").change();
			
			$("[name=PR_Rate]").val("1");
			
			$("[name='RequesAccording'][value='內部需求']").prop("checked",true);
		}
		//重送另起啟單




		else if ( Refill == "1" || Refill == "3" ){
			detailData = GetBPMDetail({Identify:'S_MM_PRA', RequisitionID:RequisitionID});
			loadDetailItem(detailData);
		}

		var ReturnAjax = "";
		$.ajax({
			type: "POST",
			async:false,
			data: { 
				ApplicantName: $("[name=ApplicantName]").val(),				
				//DapertmentCode : $("[name=ApplicantDept]").val(),			
				SelMode : "撈成本中心代碼與內部訂單"
			},
			url: "CYP_AutoScript.aspx",
			success: function(result){ //成功得到資料
				ReturnAjax = result;
			}
		});		
		if( ReturnAjax == "" )
			alert("後台[成本中心代碼]與[內部訂單]沒有對應的申請人部門資料請財務人員於BPM上協助新增");

		else{
			ApplicantCostCenterCode = ReturnAjax.split(",").shift();
			$("[name=CostCenterCode]").val(ApplicantCostCenterCode);
			
			//$("[name=BudgetOrderNo]").val(ReturnAjax.split(",").pop());
			/*
			var BudgetOrderNoVal = $("#BudgetOrderNo option").map(function(){
										return $(this).val();
									}).get().join(",")
			
			if( BudgetOrderNoVal.indexOf(ReturnAjax.split(",").pop()) == -1 )
				alert("後台[預算]沒有對應的內部訂單資料請財務人員於BPM上協助新增");
			else
				$("[name=BudgetOrderNo]").val(ReturnAjax.split(",").pop());
				
			*/	
		}
		//新建預設新增一列 -
		if ($('#DetailTable').length == 2 ){
			bpm.detail.addItem('Detail');
		}
		
	}
	else if( bpm.formInfo.processID == 'SpcMem01' )//業務關卡
	{ 
	
		if( $("[name='RequesAccording']:checked").val() == "外部需求" )
		{
			$("#PaymentTypeTD").attr("style","background-color:#FFFFFF");		
			$("[name=PaymentType]").removeAttr("disabled");
			$("[name=PaymentType]").change();
			
		}
		$("[hideinput=hideinput]").each(function(){
			hideInput($(this),"black");
		});			
		$("[hideradio=hideradio]").each(function(){
			hideRadio($(this),"black");
		});			
		$("[hideDroplist=hideDroplist]").each(function(){
			if( $(this).val() != null )
				hideDroplist($(this),"black");
			else
				$(this).hide();
		});		
		$("[hidecheckbox=hidecheckbox]").each(function(){
			$(this).hide();
		});	
		ProcessHide();
	}
	else if( bpm.formInfo.processID == 'SpcRol07' )//品保人員補充資料
	{	
		$("[name=AdjustMachineNoTD]").attr("style","background-color:#FFFFFF");
		$("[name=AdjustMachineNo]").removeAttr("disabled");
		
		$("[hideinput=hideinput]").each(function(){
			hideInput($(this),"black");
		});			
		$("[hideradio=hideradio]").each(function(){
			hideRadio($(this),"black");
		});			
		$("[hideDroplist=hideDroplist]").each(function(){
			if( $(this).val() != null )
				hideDroplist($(this),"black");
			else
				$(this).hide();
		});		
		$("[hidecheckbox=hidecheckbox]").each(function(){
			$(this).hide();
		});	
		ProcessHide();
	
	}
	else if( bpm.formInfo.processID == 'SpcRol08' )//總務人員補充資料
	{	

		if($("[name=SecondGrade]").val()=="3A"||$("[name=SecondGrade]").val()=="3B"|| $("[name=SecondGrade]").val()=="3C")		
		{
			$("[name=AUC_No]").attr("style","background-color:#FFFFFF");
			$("[name=AUC_No]").removeAttr("disabled");
		}
		
		$("[hideinput=hideinput]").each(function(){
			hideInput($(this),"black");
		});			
		$("[hideradio=hideradio]").each(function(){
			hideRadio($(this),"black");
		});			
		$("[hideDroplist=hideDroplist]").each(function(){
			if( $(this).val() != null )
				hideDroplist($(this),"black");
			else
				$(this).hide();
		});		
		$("[hidecheckbox=hidecheckbox]").each(function(){
			$(this).hide();
		});	
		ProcessHide();
	}
	else if( bpm.formInfo.processID == 'SpcMem12' )//採購人員補充資料
	{	
		
		$('[name=GuessCom]').attr('disabled',false);
		$('[name=GuessCost]').attr('disabled',false);
		$("[hideinput=hideinput]").each(function(){
			if( $(this).attr("name").indexOf("GuessCom") == -1 && $(this).attr("name").indexOf("GuessCost") == -1 )
				hideInput($(this),"black");
		});			
		$("[hideradio=hideradio]").each(function(){
			hideRadio($(this),"black");
		});			
		$("[hideDroplist=hideDroplist]").each(function(){
			if( $(this).val() != null )
				hideDroplist($(this),"black");
			else
				$(this).hide();
		});		
		$("[hidecheckbox=hidecheckbox]").each(function(){
			$(this).hide();
		});	
		ProcessHide();
	
	}
	
	else if( bpm.formInfo.processID == 'SpcMem13' )//總務XXX補充資料(模具尾關)
	{	
		
		$('[name=AUC_No]').attr('disabled',false);
		
		$("[hideinput=hideinput]").each(function()
		{
			if( $(this).attr("name").indexOf("AUC_No") == -1)
			{
				hideInput($(this),"black");
			}
		});			
		
		$("[hideradio=hideradio]").each(function()
		{
			hideRadio($(this),"black");
		});	
		
		$("[hideDroplist=hideDroplist]").each(function()
		{
			if( $(this).val() != null )
			{
				hideDroplist($(this),"black");
			}
			else
			{
				$(this).hide();
			}
		});		
		
		$("[hidecheckbox=hidecheckbox]").each(function()
		{
			$(this).hide();
		});	
		
		ProcessHide();
	
	}
	
	else{	  
		$("[hideinput=hideinput]").each(function(){
			hideInput($(this),"black");
			//console.log($(this).attr("name"));
		});			
		$("[hideradio=hideradio]").each(function(){
			hideRadio($(this),"black");
		});			
		$("[hideDroplist=hideDroplist]").each(function(){
			//console.log($(this).val());
			if( $(this).val() != null )
				hideDroplist($(this),"black");
			else
				$(this).hide();
		});		
		$("[hidecheckbox=hidecheckbox]").each(function(){
			$(this).hide();
		});	
		ProcessHide();

		//$('#Detail').find('tr th:nth-child(4),tr td:nth-child(4)').hide();
	}
	
	//form load --------------------------------------------------
	bpm.load();
});


function loadDetailNo(){
	$('[name=DetailItem][detailtype=item] [name=tdSid]').each(function(i){
		var o = $(this);
		$(o).val(i+1);
		hideEdit(o);
	});
}


function BlankClear(txt){
	txt = txt.replace(/[\r\n]/g,'');
	while( txt.indexOf(' ') == 0 ){
		txt = txt.replace(' ','');
	}
	while( txt.lastIndexOf(' ') == ( txt.length - 1 ) ){
		txt = txt.substring(0,txt.length-1);
	}
	return txt;
}


function ProcessHide(){
	$('[name=imgAddDetail]').hide();
	$('[name=imgDelDetail]').hide();
	$('[name=PR_MaterielBtn]').hide();
	$('[name=MaterielGroupBtn]').hide();
}


function InsDTable(){
	
	var bpm = $bpm();
	
	//儲存 D 表 -
	var itemList = [];
	var tdSid;
	var PR_Materiel;
	var Short_Text;
	var PurchaseGroupName;
	var PurchaseGroupCode;
	var Quantity;
	var D_PR_Amount;
	var CostCenterName;
	var CostCenterCode;
	var PR_D_Remark;
	var AUC_No;
	var DeliverDate;
	var MaterielGroupName;
	var MaterielGroupCode;
	var ProposeStores;
	var ProjectOrderNo;
	var MeasureUnit;
	var PR_D_TotalAmount;
	var BudgetOrderNo;
	var AdjustMachineNo;
	var GuessCom;
	var GuessCost;
	
	$('[name=DetailItem][detailtype=item]').each(function(i){
		
		var TmpI = i + 1;
		
		if( TmpI % 2 != 0 ){
			tdSid = $(this).find('[name=tdSid]').val();
			PR_Materiel = $(this).find('[name=PR_Materiel]').val();
			Short_Text = $(this).find('[name=Short_Text]').val();
			PurchaseGroupName = $(this).find('[name=PurchaseGroupName]').val();
			PurchaseGroupCode = $(this).find('[name=PurchaseGroupCode]').val();
			Quantity = $(this).find('[name=Quantity]').val();
			D_PR_Amount = $(this).find('[name=D_PR_Amount]').val();
			CostCenterName = $(this).find('[name=CostCenterName]').val();
			CostCenterCode = $(this).find('[name=CostCenterCode]').val();
			PR_D_Remark = $(this).find('[name=PR_D_Remark]').val();
			AUC_No = $(this).find('[name=AUC_No]').val();
			GuessCom =  $(this).find('[name=GuessCom]').val();
		}
		else{
			DeliverDate = $(this).find('[name=DeliverDate]').val();
			MaterielGroupName = $(this).find('[name=MaterielGroupName]').val();
			MaterielGroupCode = $(this).find('[name=MaterielGroupCode]').val();
			ProposeStores = $(this).find('[name=ProposeStores]').val();
			ProjectOrderNo = $(this).find('[name=ProjectOrderNo]').val();
			MeasureUnit = $(this).find('[name=MeasureUnit]').val();
			PR_D_TotalAmount = $(this).find('[name=PR_D_TotalAmount]').val();
			BudgetOrderNo = $(this).find('[name=BudgetOrderNo]').val();
			AdjustMachineNo = $(this).find('[name=AdjustMachineNo]').val();
			GuessCost =  $(this).find('[name=GuessCost]').val();
			
			itemList.push({
				RequisitionID:bpm.formInfo.requisitionID,
				tdSid:tdSid,
				PR_Materiel:PR_Materiel,
				Short_Text:Short_Text,
				PurchaseGroupName:PurchaseGroupName,
				PurchaseGroupCode:PurchaseGroupCode,
				Quantity:Quantity,
				D_PR_Amount:D_PR_Amount,
				CostCenterName:CostCenterName,
				CostCenterCode:CostCenterCode,
				DeliverDate:DeliverDate,
				AUC_No:AUC_No,
				MaterielGroupName:MaterielGroupName,
				MaterielGroupCode:MaterielGroupCode,
				ProposeStores:ProposeStores,
				ProjectOrderNo:ProjectOrderNo,
				MeasureUnit:MeasureUnit,
				PR_D_TotalAmount:PR_D_TotalAmount,
				BudgetOrderNo:BudgetOrderNo,
				PR_D_Remark:PR_D_Remark,
				AdjustMachineNo:AdjustMachineNo,
				GuessCom:GuessCom,
				GuessCost:GuessCost
			});
		}
	});
	DelBPMDetail({table:'FM7T_S_MM_PRA_D', itemList:JSON.stringify([{RequisitionID:bpm.formInfo.requisitionID}])});
	InsBPMDetail({table:'FM7T_S_MM_PRA_D', itemList:JSON.stringify(itemList)});
}


function TotalAmount(){
	var TotalAmount = 0;
	$("[name=Quantity]").each(function(i){
		if( $(this).val() != "" ){
			//if( $(this).closest('tr').find('[name=D_PR_Amount]').val() == "" )
			//	$(this).closest('tr').find('[name=D_PR_Amount]').val("1");
			if( $(this).closest('tr').find('[name=D_PR_Amount]').val() != "" ){
				var TmpAMT = FloatMul($(this).val(),$(this).closest('tr').find('[name=D_PR_Amount]').val());			
				TotalAmount = FloatAdd(TotalAmount,TmpAMT);
			}
		}
	});	
	$("[name=PRTotalAmount]").val(FloatMul(TotalAmount,$("[name=PR_Rate]").val()));
}

</script>

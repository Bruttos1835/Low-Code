/*
 * Author       : felipe.brito_ttwgroup
 * Generated on : 24-Nov-2023 05:13:37
 * Version      : 1.0
 */
 application "Controle de Estoque"
 {
 	date format = "dd-MMM-yyyy"
 	time zone = "America/Sao_Paulo"
 	time format = "24-hr"
 	section Lojas
	{
		icon = "tech-desktop"
		form Lojas
		{
			success message = "Dados adicionados com sucesso!"
			field alignment = left
			Section
			(
				type = section
	 			row = 1
	 			column = 0   
				width = medium
			)
			must have Nome
			(
    			type = text
	 			row = 1
	 			column = 1   
				width = medium
			)
			Endere_o
			(
    			type = address
				displayname = "Endereço"
     			capture_coordinates = true
     			adjust_using_map = false
     			address_line_1
     			(
	     			  type = address_line_1
	     			  displayname = "Address Line 1"
     			) 
     			address_line_2
     			(
	     			  type = address_line_2
	     			  displayname = "Address Line 2"
     			) 
     			district_city
     			(
	     			  type = district_city
	     			  displayname = "City / District"
     			) 
     			state_province
     			(
	     			  type = state_province
	     			  displayname = "State / Province"
     			) 
     			postal_Code
     			(
	     			  type = postal_Code
	     			  displayname = "Postal Code"
     			) 
     			country
     			(
	     			  type = country
	     			  displayname = "Country"
     			) 
     			latitude
     			(
	     			  type = latitude
	     			  displayname = "latitude"
	     			 visibility = false
     			) 
     			longitude
     			(
	     			  type = longitude
	     			  displayname = "longitude"
	     			 visibility = false
     			) 
	 			row = 1
	 			column = 1   
				width = medium
				personal data = true
			)
			must have Email
			(
    			type = email
				maxchar = 80
	 			row = 1
	 			column = 1   
				width = medium
				personal data = true
			)
			Telefone
			(
    			type = phonenumber
    			allowedcountries={br}
    			defaultcountry="br"
	 			row = 1
	 			column = 1   
				width = medium
				personal data = true
			)
	
			customize
			(
				icon = "ui-1-bold-add"
			)
			actions
			{
				on add
				{
					submit
					(
   						type = submit
   						displayname = "Enviar"
					)
					reset
					(
   						type = reset
   						displayname = "Restaurar"
					)
				}
				on edit
				{
					update
					(
   						type = submit
   						displayname = "Atualizar"
					)
					cancel
					(
   						type = cancel
   						displayname = "Cancelar"
					)
				}
			}
		}
		default list Lojas_Report
		{
			displayName = "Lojas Relatório"
			show all rows from Lojas    
			(
				Nome
				Email
				Endere_o  as "Endereço"
	 			(
	      			displayformat = [address_line_1+""+address_line_2+""+district_city+""+state_province+""+postal_Code+""+country]
	      			enable = Link_to_Map,Show_As_Text
	 			)
				Telefone
				(
					displayformat = plainnumber 
					linktodial = enable
				)
			)
			options
			(
				icon = "design-bullet-list-67"
	 		)
			quickview
			(
				layout
				(
		 			type = -1
					datablock1
					(
						layout type = -1
						fields
						(
							Nome
							Email
							Endere_o as "Endereço"
							Telefone
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
					record
					(
						Edit   	   
						Duplicate   	   
						Delete   	   
    				)
    			)
    			action
    			(
					on click
					(
						View Record   	   
    				)
					on right click
					(
						Edit   	   
						Delete   	   
						Duplicate   	   
						View Record   	   
    				)
     			)
			)
			detailview
			(
				layout
				(
		 			type = 1
					datablock1
					(
						layout type = -2
						fields
						(
							Nome
							Email
							Endere_o as "Endereço"
							Telefone
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
    			)
			)
		}
	}
	section Produtos
	{
		icon = "tech-desktop"
		form Produtos
		{
			success message = "Dados adicionados com sucesso!"
			field alignment = left
			Section
			(
				type = section
	 			row = 1
	 			column = 0   
				width = medium
			)
			must have Nome
			(
    			type = text
	 			row = 1
	 			column = 1   
				width = medium
			)
			must have unique Codigo
			(
    			type = text
				displayname = "Código"
	 			row = 1
	 			column = 1   
				width = medium
			)
			Image
			(
    			type = image
				source  = file
				aspect ratio = original
				camera = primary
				show gallery = true
				switch camera = true
	 			row = 1
	 			column = 1   
				width = medium
			)
			Lojas
			(
				type = picklist	
				values  = Lojas.ID
    			displayformat = [Nome]
				searchable = true
				sortorder = ascending
	 			row = 1
	 			column = 1   
				width = medium
			)
			Total_em_estoque
			(
				type = number
				displayname = "Total em estoque"
				initial value = 0
	 			row = 1
	 			column = 1   
				width = medium
			)
	
			customize
			(
				icon = "ui-1-bold-add"
			)
			actions
			{
				on add
				{
					submit
					(
   						type = submit
   						displayname = "Enviar"
					)
					reset
					(
   						type = reset
   						displayname = "Restaurar"
					)
				}
				on edit
				{
					update
					(
   						type = submit
   						displayname = "Atualizar"
					)
					cancel
					(
   						type = cancel
   						displayname = "Cancelar"
					)
				}
			}
		}
		default list Produtos_Report
		{
			displayName = "Produtos Relatório"
			show all rows from Produtos    
			(
				Nome
				Codigo as "Código"
				Image
				Lojas
				Total_em_estoque as "Total em estoque"
			)
			options
			(
				icon = "design-bullet-list-67"
	 		)
			quickview
			(
				layout
				(
		 			type = -1
					datablock1
					(
						layout type = -1
						fields
						(
							Nome
							Codigo as "Código"
							Image
							Lojas
							Total_em_estoque as "Total em estoque"
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
					record
					(
						Edit   	   
						Duplicate   	   
						Delete   	   
    				)
    			)
    			action
    			(
					on click
					(
						View Record   	   
    				)
					on right click
					(
						Edit   	   
						Delete   	   
						Duplicate   	   
						View Record   	   
    				)
     			)
			)
			detailview
			(
				layout
				(
		 			type = 1
					datablock1
					(
						layout type = -2
						fields
						(
							Nome
							Codigo as "Código"
							Image
							Lojas
							Total_em_estoque as "Total em estoque"
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
    			)
			)
		}
	}
	section Entrada_de_Produto
	{
		displayname= "Entrada de Produto"
		icon = "sport-fencing"
		form Entrada_de_Produto
		{
			displayname = "Entrada de Produto"
			success message = "Dados adicionados com sucesso!"
			field alignment = left
			Section
			(
				type = section
	 			row = 1
	 			column = 0   
				width = medium
			)
			must have Produtos
			(
				type = picklist	
				values  = Produtos.ID
    			displayformat = [Codigo + " - " + Nome]
				sortorder = ascending
	 			row = 1
	 			column = 1   
				width = medium
			)
			must have Quantidade_adquirido
			(
				type = number
				displayname = "Quantidade adquirido"
	 			row = 1
	 			column = 1   
				width = medium
			)
	
			customize
			(
				icon = "sport-fencing"
			)
			actions
			{
				on add
				{
					submit
					(
   						type = submit
   						displayname = "Enviar"
					)
					reset
					(
   						type = reset
   						displayname = "Restaurar"
					)
				}
				on edit
				{
					update
					(
   						type = submit
   						displayname = "Atualizar"
					)
					cancel
					(
   						type = cancel
   						displayname = "Cancelar"
					)
				}
			}
		}
		default list Entrada_de_Produto_Report
		{
			displayName = "Entrada de Produto Relatório"
			show all rows from Entrada_de_Produto    
			(
				Produtos
				Quantidade_adquirido as "Quantidade adquirido"
			)
			options
			(
				icon = "sport-fencing"
	 		)
			quickview
			(
				layout
				(
		 			type = -1
					datablock1
					(
						layout type = -1
						fields
						(
							Produtos
							Quantidade_adquirido as "Quantidade adquirido"
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
					record
					(
						Edit   	   
						Duplicate   	   
						Delete   	   
    				)
    			)
    			action
    			(
					on click
					(
						View Record   	   
    				)
					on right click
					(
						Edit   	   
						Delete   	   
						Duplicate   	   
						View Record   	   
    				)
     			)
			)
			detailview
			(
				layout
				(
		 			type = 1
					datablock1
					(
						layout type = -2
						fields
						(
							Produtos
							Quantidade_adquirido as "Quantidade adquirido"
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
    			)
			)
		}
	}
	section Sa_da_de_Produto
	{
		displayname= "Saída de Produto"
		icon = "sport-fencing"
		form Sa_da_de_Produto
		{
			displayname = "Saída de Produto"
			success message = "Dados adicionados com sucesso!"
			field alignment = left
			Section
			(
				type = section
	 			row = 1
	 			column = 0   
				width = medium
			)
			must have Produtos
			(
				type = picklist	
				values  = Produtos.ID
    			displayformat = [Codigo + " - " + Nome]
				sortorder = ascending
	 			row = 1
	 			column = 1   
				width = medium
			)
			must have Quantidade
			(
				type = number
				displayname = "Quantidade Vendida"
	 			row = 1
	 			column = 1   
				width = medium
			)
	
			customize
			(
				icon = "sport-fencing"
			)
			actions
			{
				on add
				{
					submit
					(
   						type = submit
   						displayname = "Enviar"
					)
					reset
					(
   						type = reset
   						displayname = "Restaurar"
					)
				}
				on edit
				{
					update
					(
   						type = submit
   						displayname = "Atualizar"
					)
					cancel
					(
   						type = cancel
   						displayname = "Cancelar"
					)
				}
			}
		}
		default list Sa_da_de_Produto_Report
		{
			displayName = "Saída de Produto Relatório"
			show all rows from Sa_da_de_Produto    
			(
				Produtos
				Quantidade as "Quantidade Vendida"
			)
			options
			(
				icon = "sport-fencing"
	 		)
			quickview
			(
				layout
				(
		 			type = -1
					datablock1
					(
						layout type = -1
						fields
						(
							Produtos
							Quantidade as "Quantidade Vendida"
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
					record
					(
						Edit   	   
						Duplicate   	   
						Delete   	   
    				)
    			)
    			action
    			(
					on click
					(
						View Record   	   
    				)
					on right click
					(
						Edit   	   
						Delete   	   
						Duplicate   	   
						View Record   	   
    				)
     			)
			)
			detailview
			(
				layout
				(
		 			type = 1
					datablock1
					(
						layout type = -2
						fields
						(
							Produtos
							Quantidade as "Quantidade Vendida"
						)
					)
				)
				menu
    			(
    	 			header
    	 			(
    		 			Edit 
    		 			Duplicate 
    		 			Delete 
    	 			)
    			)
			)
		}
	}






		workflow
		{
		form
		{
			Add_estoque as "Add estoque"
			{
				type =  form
				form = Entrada_de_Produto
				record event = on add

				on success
				{
					actions 
					{
						custom deluge script
						(
											umProduto = Produtos[ID == input.Produtos];
										umProduto.Total_em_estoque=umProduto.Total_em_estoque + input.Quantidade_adquirido;
						)
					}
				}

			}
			Remover_estoque as "Remover estoque"
			{
				type =  form
				form = Sa_da_de_Produto
				record event = on add

				on success
				{
					actions 
					{
						custom deluge script
						(
											umProduto = Produtos[ID == input.Produtos];
										umProduto.Total_em_estoque=umProduto.Total_em_estoque - input.Quantidade;
						)
					}
				}

			}
		}





	}
	share_settings
	{
			"Read"
			{
				name = "Read"
				type = Users_Permissions
				permissions = {Chat:true, Predefined:true, ApiAccess:true, PIIAccess:true, ePHIAccess:true}
				description = "This profile will have read permission for all components\n"
			}
			"Write"
			{
				name = "Write"
				type = Users_Permissions
				permissions = {Chat:true, Predefined:true, ApiAccess:true, PIIAccess:true, ePHIAccess:true}
				description = "This profile will have write permission for all components\n"
			}
			"Administrator"
			{
				name = "Administrator"
				type = Users_Permissions
				permissions = {Chat:true, Predefined:true, ApiAccess:true, PIIAccess:true, ePHIAccess:true}
				description = "This profile will have all the permissions.\n"
			}
			"Customer"
			{
				name = "Customer"
				type = Customer_Portal
				permissions = {Chat:true, Predefined:true, ApiAccess:true, PIIAccess:true, ePHIAccess:true}
				description = "This is the default profile having only add and view permission.\n"
			}
			roles
			{
				"CEO"
				{
					description = "User belonging to this role can access data of all other users."
				}
			}
	}

	customize
	{
		
		layout = "tab"
		color = "black"
		base theme = "professional"
		new theme = 8
		icons = true
		icons style = outline
		font = "lato"
		color options
    	{
        color = "1"
    	}
    	logo
    	{
        	preference = "app_icon"
        	placement = "left"
    	}
	}


	phone
	{
		customize
		{
        	layout = slidingpane
		 	icons style = outline
        	font = "default"
            style = "3"
        	color options
        	{
             	color = amethyst
         	}
         	logo
         	{
             	preference = "none"
         	}
		}
	}
	tablet
	{
		customize
		{
        	layout = slidingpane
		 	icons style = outline
        	font = "default"
            style = "3"
        	color options
        	{
             	color = amethyst
         	}
         	logo
         	{
             	preference = "none"
         	}
		}
	}
	
}

# One_hot_encode


def onehot(df,features):
    df=df.copy()
    for feature in features : 
        cats=list(df.loc[:,feature].unique())
        if len(cats)==1 :
            continue 
            
        loc=df.columns.get_loc(feature) 
        [df.insert(loc=loc,column='{}_{}'.format(feature,cat),value=0.0) for cat in cats[:-1]]  
        for index in df.index :
            val=df.loc[index,feature] 
            clm='{}_{}'.format(feature,val) 
            if clm in df.columns :
                df.loc[index,clm]=1.0 
            
        df=df.drop(columns=[feature]) 
        
    
        
    return df
